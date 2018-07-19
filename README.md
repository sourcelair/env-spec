# Env Spec

Env Spec lets you declare the required environment variable configuration of your application in a minimalistic language.


## Example

```
ADMIN_EMAIL: email
ADMIN_NAME
DATABASE_URL: url
DEBUG: [0,1]=1
ENVIRONMENT: [production,staging,development]=development
TWILIO_API_KEY
```

## Objectives

- A valid `.env.spec` file should be able to be converted deterministically to an HTML form

## Variable names

Every line in a `.env.spec` file should start with the name of the requested environment variable. Valid variable names should comply with the following rules

- They contain only uppercase latin characters, numeric digits and underscores
- They do not start with a numeric digit
- They do not exceed 64 characters in length

### Valid variable name examples

- `ENVIRONMENT`
- `ADMIN_EMAIL`
- `POSTGRES_10_PASSWORD`
- `_TEMPORARY_TEST`

### Invalid variable name examples

- `ΜΕΤΑΒΛΗΤΟΥΛΑ`
- `42`
- `ADMIN-EMAIL`

## Types

Types can be used optionally in `.env.spec` in order to enforce input validation.

The available types that can be used in an `.env.spec` file are the following:

- `color`
- `date`
- `datetime-local`
- `email`
- `month`
- `number`
- `password`
- `tel`
- `text`
- `time`
- `url`
- `week`

### Example `.env.spec` with types

```
ADMIN_EMAIL: email
DATABASE_URL: url
DEBUG: number
ENVIRONMENT: text
```

## Restricted choices

To enforce stricter validation, the available values for a particular variable can be restricted to enumerated choices.

**👋Heads up!** When defining the available choices for a variable, you cannot define a type for it. This would be completely redundant, since the end-user cannot submit invalid data, because the available choices are restricted up front.

### Choices in .env.spec

```
ADMIN_EMAIL: email
DATABASE_URL: url=postgres://USER:PASSWORD@HOST:PORT/NAME
DEBUG: [0,1]
ENVIRONMENT: [production,staging,development]
```

## Default values

To help end-users save time, defaults can be declared and set as values, where it makes sense.

### Defaults in .env.spec

```
ADMIN_EMAIL: email
DATABASE_URL: url=postgres://USER:PASSWORD@HOST:PORT/NAME
DEBUG: [0,1]=1
ENVIRONMENT: [production,staging,development]=development
```


## Comments

Comments can be used to provide helpful human-readable information for an `.env.spec` entry.

Use the hash symbol marks the rest of a line as a comment.

### Example `.env.spec` with comments

```
ADMIN_EMAIL: email  # This email will be notified when exceptions get raised
DATABASE_URL: url=postgres://USER:PASSWORD@HOST:PORT/NAME
DEBUG: [0,1]=1  # Switching debug on emits verbose messages in the terminal
ENVIRONMENT: [production,staging,development]=development
```

## File name

Files containing in the Env Spec file format should be named `.env.spec` exclusively.

## License

Licensed under the [MIT License](LICENSE)
