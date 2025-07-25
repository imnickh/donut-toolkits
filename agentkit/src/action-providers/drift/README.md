# Drift Action Provider

This directory contains the **DriftActionProvider** implementation, which provides actions for drift operations.

## Overview

The DriftActionProvider is designed to work with SvmWalletProvider for blockchain interactions. It provides a set of actions that enable [describe the main purpose/functionality].

## Directory Structure

```
drift/
├── driftActionProvider.ts       # Main provider implementation
├── driftActionProvider.test.ts  # Provider test suite
├── exampleAction.test.ts           # Example action test suite
├── schemas.ts                      # Action schemas and types
├── index.ts                        # Package exports
└── README.md                       # Documentation (this file)
```

## Actions

### Example Action
- `example-action`: Template action implementation
  - **Purpose**: Demonstrates the basic structure of an action
  - **Input**:
    - `fieldName` (string): A descriptive name for the field (1-100 chars)
    - `amount` (string): The amount as a decimal string (e.g. "1.5")
    - `optionalField` (string, optional): Optional parameter example
  - **Output**: String describing the action result
  - **Example**:
    ```typescript
    const result = await provider.exampleAction(walletProvider, {
      fieldName: "test",
      amount: "1.0"
    });
    ```

## Implementation Details

### Network Support
This provider supports all svm networks.

### Wallet Provider Integration
This provider is specifically designed to work with SvmWalletProvider. Key integration points:
- Network compatibility checks
- Transaction signing and execution
- Balance and account management

## Adding New Actions

To add new actions:

1. Define the schema in `schemas.ts`:
   ```typescript
   export const NewActionSchema = z.object({
     // Define your action's parameters
   });
   ```

2. Implement the action in `driftActionProvider.ts`:
   ```typescript
   @CreateAction({
     name: "new_action",
     description: "Description of what your action does",
     schema: NewActionSchema,
   })
   async newAction(
walletProvider: SvmWalletProvider,      args: z.infer<typeof NewActionSchema>
   ): Promise<string> {
     // Implement your action logic
   }
   ```

## Testing

When implementing new actions, ensure to:
1. Add unit tests for schema validations
2. Test network support

## Notes

- Add any specific considerations for this action provider
- Document any prerequisites or setup requirements
- Include relevant external documentation links
