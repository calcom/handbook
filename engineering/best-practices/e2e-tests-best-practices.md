---
description: >-
  These are some basic principles that should be respected when working with E2E
  tests. Failure to follow these practices can be a motive for PR rejection.
---

# E2E Tests Best Practices

* A test should avoid using Text Locators: `page.locator('text=`
  * Add a proper to data-testid to the HTML element and retrieve it by using page.getByTestId
  * From [Playwright docs](https://playwright.dev/docs/locators#locate-by-test-id):
    * > Testing by test ids is the most resilient way of testing as even if your text or role of the attribute changes the test will still pass. QA's and developers should define explicit test ids and query them with page.getByTestId(). However testing by test ids is not user facing. If the role or text value is important to you then consider using user facing locators such as role and text locators.
* A test should be able to run locally as well as on CI
* A test should be able to be run multiple times and expect a consistent result
* A test should not introduce side-effects that may affect other tests running in parallel
* A test should use expect(page).toHaveURL() so we can fail fast if a new unexpected redirection is introduced
* A test should avoid using fixed seeded records for testing.
  * This conflicts with parallelization and consistency
* A test should reset the DB state to be the same after running tests than it was before running them.
  * This means all created records should be properly cleaned up after tests are run
  * If seeded records were used, return them to their original state afterwards.

### TODO

* Guide for debugging E2E failures
  * What to do when checks fail?
  * How can I know where to look?
* Recommended Tools and extensions
* Workflow recommendations for working with E2E tests
