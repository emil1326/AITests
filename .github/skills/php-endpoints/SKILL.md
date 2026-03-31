---
name: php-endpoints
description: Build and review plain PHP endpoints for forms, fetch requests, validation, and shared hosting.
---

# PHP Endpoints Skill

Use this skill when the task touches backend PHP files or API endpoints.

## When to Use This Skill

- You need a form handler, fetch endpoint, or webhook in plain PHP.
- You need request validation before persistence.
- You need a response shape a frontend can consume safely.
- You need shared-hosting-friendly PHP rather than framework code.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Read the PHP file instructions.
- Check how the frontend will call the endpoint.

## What This Skill Is For

- Building small form handlers or JSON endpoints.
- Keeping request parsing, validation, and persistence explicit.
- Making shared-hosting-safe PHP endpoints that are easy to debug.
- Avoiding framework-level complexity when plain PHP is enough.

## Request Flow Checklist

- What method will the client send?
- What fields are required?
- What should a bad request return?
- What should a success response look like?
- What persistence or side effects happen after validation?

## Controlled Flow

1. Identify the request source: form submit, fetch call, webhook, or direct browser hit.
2. Validate method, content type, and required fields before any business logic.
3. Normalize inputs and reject bad data early.
4. Perform the database or file operation with the safest available primitive.
5. Return a response shape that the frontend can consume without guessing.
6. Keep the file small enough that the control flow is obvious at a glance.

## Hard Limits

- Do not read from `$_POST` or `$_GET` without validation.
- Do not interpolate SQL strings.
- Do not return ambiguous success responses that hide real failures.
- Do not depend on framework helpers that do not exist in plain PHP.

## Concrete Patterns

### Good: JSON Form Handler

```php
<?php
declare(strict_types=1);

header('Content-Type: application/json; charset=utf-8');

if ($_SERVER['REQUEST_METHOD'] !== 'POST') {
	http_response_code(405);
	echo json_encode(['ok' => false, 'error' => 'Method not allowed']);
	exit;
}

$email = filter_input(INPUT_POST, 'email', FILTER_VALIDATE_EMAIL);
$message = trim((string)($_POST['message'] ?? ''));

if ($email === false || $message === '') {
	http_response_code(400);
	echo json_encode(['ok' => false, 'error' => 'Invalid input']);
	exit;
}

$stmt = $pdo->prepare('INSERT INTO contacts (email, message) VALUES (:email, :message)');
$stmt->execute([
	'email' => $email,
	'message' => $message,
]);

echo json_encode(['ok' => true]);
```

Why this is good:

- The method gate is explicit.
- Inputs are validated before use.
- The SQL is parameterized.
- The response is easy for the frontend to handle.

### Bad: Unvalidated SQL and Loose Responses

```php
<?php
$pdo->query("INSERT INTO contacts VALUES ('{$_POST['email']}', '{$_POST['message']}')");
echo 'ok';
```

Why this is bad:

- It trusts raw input.
- It is vulnerable to injection.
- It gives the frontend no reliable response shape.

## Validation

- Request method is checked.
- Inputs are validated and normalized.
- SQL uses prepared statements.
- Status codes match the outcome.
- The frontend can reliably interpret success and failure.

## Output Contract

- Endpoint changes and safety notes.
- Request/response contract.
- Validation performed.
- File and line references when possible.
- Follow-up concerns if the request flow is incomplete.
