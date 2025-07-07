# FollowBotMobile
We are developing a mobile app that is meant to interface with your fellow FollowBot. You will be able to access everything from data analytics, to the location of your FollowBot. The goal for the mobile app is to ensure that the user does not need to bring their computer wherever they go with the FollowBot. That was the intended goal and will be the final goal for our FollowBot. 

It is important to remember that whatever is on the Website that is related to communicating with Followbot will immediately be migrated into the mobile device itself. Certain functionalities will be kept on the Website, but most will be migrated to the mobile app instead.

## Plans for Development

We will be focusing on the main mechanics of our mobile device:
* Establishing a connection with your FollowBot
* Obtaining reliable data from your FollowBot
* Updated with essential information from your FollowBot
* Adding more FollowBots towards your network of FollowBots.
* Ensuring User friendly mechanics 

## Configuration & Usage
For installations and Configurations please follow the link below:
[Installation and Setup](https://github.com/FrankVanris2/FollowBotMobile/blob/main/BotServerNative/README.md)

## Development Guidelines

### MANDATORY: Unit Testing Before Implementation

**Every developer MUST implement comprehensive unit tests before adding any new feature to the codebase.**

#### Testing Requirements:

1.  **Write Tests First**: Follow **Test-Driven Development (TDD)** principles.

      * Write failing tests that describe the expected behavior.
      * Implement the minimum code to make tests pass.
      * Refactor while keeping tests green.

2.  **Test Coverage Requirements**:

      * All new functions/methods must have corresponding unit tests.
      * Minimum **80% code coverage** for new features.
      * Test both success and failure scenarios.
      * Mock external dependencies (API requests, device features, etc.).

3.  **Testing Standards**:

      * Use **Jest** for all TypeScript and React Native components.
      * Follow naming convention: \`[component/functionName].test.ts\` or \`[component/functionName].test.tsx\`.
      * Include setup and teardown for test isolation.

4.  **Before Pull Request**:

    ```bash
    # Run all unit tests to ensure nothing is broken
    npm test

    # Verify the mobile app builds successfully
    npm run build:ios # Or npm run build:android, depending on your build scripts
    ```

5.  **Test Documentation**:

      * Document test scenarios in commit messages.
      * Update test documentation when adding new test patterns.
      * Reference **[Jest Unit Testing Guide for TypeScript Mobile Apps](https://github.com/FrankVanris2/FollowBotWebsite/blob/main/Documentation/JestUnitTesting.md)**

#### Example Test Structure:

```typescript
// For React Native components
import { render, screen } from '@testing-library/react-native';
import UserLogin from '../src/components/UserLogin'; // Adjust path as needed

describe('<UserLogin />', () => {
  test('should render login form correctly', () => {
    render(<UserLogin />);
    expect(screen.getByPlaceholderText('Email')).toBeTruthy();
    expect(screen.getByPlaceholderText('Password')).toBeTruthy();
    expect(screen.getByText('Login')).toBeTruthy();
  });

  test('should display error for invalid credentials', async () => {
    render(<UserLogin />);
    // Simulate user input and interaction leading to an error
    // For example, fireEvent.changeText on input fields, then fireEvent.press on login button
    // Await for error message to appear
    expect(await screen.findByText('Invalid credentials')).toBeTruthy();
  });
});

// For utility functions or Redux slices
import { sum } from '../src/utils/math'; // Adjust path as needed

describe('sum function', () => {
  test('should correctly add two positive numbers', () => {
    expect(sum(2, 3)).toBe(5);
  });

  test('should handle negative numbers', () => {
    expect(sum(-1, 5)).toBe(4);
  });
});
```

**No feature will be merged without corresponding unit tests. This ensures code reliability and maintainability for our mobile application.**

