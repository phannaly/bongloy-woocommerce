---
name: add-or-update-payment-method
description: Workflow command scaffold for add-or-update-payment-method in bongloy-woocommerce.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-update-payment-method

Use this workflow when working on **add-or-update-payment-method** in `bongloy-woocommerce`.

## Goal

Adds a new payment method or updates an existing one, including backend, gateway, and supporting files.

## Common Files

- `includes/gateway/class-omise-payment-*.php`
- `includes/class-omise-payment-factory.php`
- `omise-woocommerce.php`
- `assets/css/omise-css.css`
- `assets/images/*`
- `includes/backends/class-omise-backend-*.php`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create or update gateway class in includes/gateway/class-omise-payment-*.php
- Update includes/class-omise-payment-factory.php to register the new payment method
- Update omise-woocommerce.php to reflect changes
- Optionally update assets (CSS, images) and backend files

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.