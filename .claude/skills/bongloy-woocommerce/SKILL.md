```markdown
# bongloy-woocommerce Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides guidance on contributing to the `bongloy-woocommerce` repository, a JavaScript-based WooCommerce payment plugin. It covers coding conventions, file organization, standard workflows for releases and feature development, and testing patterns. By following these patterns, contributors can ensure consistency and maintainability across the codebase.

## Coding Conventions

- **File Naming:**  
  Use **kebab-case** for all file names.
  - Example:  
    `omise-payment-method.js`, `class-omise-payment-factory.php`

- **Import Style:**  
  Use **relative imports** for JavaScript modules.
  - Example:
    ```js
    import { someFunction } from './utils/helper.js';
    ```

- **Export Style:**  
  Use **named exports** for JavaScript modules.
  - Example:
    ```js
    // utils/helper.js
    export function someFunction() { ... }
    ```

- **Commit Messages:**  
  Freeform, typically concise (average 39 characters).  
  No strict prefixing required.

## Workflows

### Release Version Update
**Trigger:** When releasing a new version of the plugin.  
**Command:** `/release`

1. Update `CHANGELOG.md` with release notes.
2. Update the version number in `omise-woocommerce.php`.
3. Update `readme.txt` with the new version and changes.

**Example:**
```md
## [1.2.3] - 2024-06-10
### Added
- Support for new payment method X
### Fixed
- Bug in mobile banking display
```
```php
// omise-woocommerce.php
* Version: 1.2.3
```

---

### Add or Update Payment Method
**Trigger:** When introducing a new payment method or making significant changes to an existing one.  
**Command:** `/add-payment-method`

1. Create or update gateway class in `includes/gateway/class-omise-payment-*.php`.
2. Update `includes/class-omise-payment-factory.php` to register the new payment method.
3. Update `omise-woocommerce.php` to reflect changes.
4. Optionally update assets (CSS, images) and backend files.

**Example:**
```php
// includes/gateway/class-omise-payment-newmethod.php
class Omise_Payment_NewMethod extends WC_Payment_Gateway { ... }
```
```php
// includes/class-omise-payment-factory.php
$methods[] = 'Omise_Payment_NewMethod';
```

---

### Update Mobile Banking or Payment Assets
**Trigger:** When updating the appearance or configuration of payment methods, especially mobile banking.  
**Command:** `/update-payment-assets`

1. Update `assets/css/omise-css.css` for styling.
2. Add or update images in `assets/images/`.
3. Modify `includes/backends/class-omise-backend-mobile-banking.php` as needed.
4. Update related gateway classes if required.

**Example:**
```css
/* assets/css/omise-css.css */
.omise-mobile-banking-logo { width: 64px; }
```

---

### GitHub Actions Release Workflow Update
**Trigger:** When improving or fixing the release automation process.  
**Command:** `/update-release-workflow`

1. Edit `.github/workflows/release.yml`.
2. Optionally edit `.github/workflows/build.yml`.
3. Optionally update `.github/CODEOWNERS`.

**Example:**
```yaml
# .github/workflows/release.yml
on:
  push:
    tags:
      - 'v*.*.*'
jobs:
  release:
    ...
```

---

### Merge Release or Feature Branch
**Trigger:** When finalizing a release or feature and merging it into the main branch.  
**Command:** `/merge-release`

1. Merge branch via pull request.
2. Update relevant files (often same as release-version-update or feature addition).
3. Resolve any conflicts.

---

## Testing Patterns

- **Framework:** [Jest](https://jestjs.io/)
- **Test File Pattern:** Files end with `.test.js`
  - Example: `payment-method.test.js`
- **Test Example:**
  ```js
  // payment-method.test.js
  import { processPayment } from './payment-method';

  test('should process payment successfully', () => {
    expect(processPayment({ amount: 100 })).toBe(true);
  });
  ```

## Commands

| Command                  | Purpose                                                        |
|--------------------------|----------------------------------------------------------------|
| /release                 | Prepare and publish a new plugin release version               |
| /add-payment-method      | Add or update a payment method and register it                 |
| /update-payment-assets   | Update mobile banking/payment assets and related backend files  |
| /update-release-workflow | Update GitHub Actions release automation                       |
| /merge-release           | Merge a release or feature branch into master                  |
```
