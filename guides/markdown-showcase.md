---
title: Markdown Feature Showcase
subtitle: Every supported format in one page
description: A comprehensive reference of all markdown and MDX features supported by the platform.
date: 2025-06-15
sidebar_position: 99
---

# Markdown Feature Showcase

This page demonstrates every markdown feature supported by the platform. For platform-specific formats (Mintlify, Docusaurus, GFM), each section shows the original source syntax in a code block followed by the rendered result.

## Standard Text Formatting

Regular paragraphs are separated by blank lines. Inline formatting includes **bold text**, *italic text*, ***bold italic***, `inline code`, and ~~strikethrough~~. Links look like [this](https://example.com).

## Headings

All six heading levels are supported. H1 is typically used as the page title.

### Third-Level Heading

#### Fourth-Level Heading

##### Fifth-Level Heading

###### Sixth-Level Heading

## Lists

### Unordered Lists

- First item with some explanation
- Second item covering a different topic
- Third item wrapping up the list

### Ordered Lists

1. Clone the repository
2. Install dependencies
3. Start the development server
4. Open the browser to verify

### Nested Lists

- Parent item one
    - Child item 1a
    - Child item 1b
        - Grandchild item
- Parent item two
    - Child item 2a

### Mixed Nesting

1. First ordered item
    - Unordered child A
    - Unordered child B
2. Second ordered item
    - Another unordered child

## Code Blocks

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"

if __name__ == "__main__":
    print(greet("World"))
```

Code blocks can include a filename after the language tag:

```typescript api/handler.ts
import { Request, Response } from 'express';

export function healthCheck(req: Request, res: Response) {
  res.json({ status: 'ok', timestamp: Date.now() });
}
```

## Tables

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/users` | List all users |
| POST | `/api/users` | Create a new user |
| GET | `/api/users/:id` | Get user by ID |
| DELETE | `/api/users/:id` | Delete a user |

## Block Quotes

> The best way to predict the future is to invent it.
> — Alan Kay

## Thematic Breaks

Content above the break.

---

Content below the break.

## Images

Standalone images are displayed as media:

![Architecture diagram](https://picsum.photos/seed/architecture/800/400)

Multiple consecutive images each display separately:

![Frontend flow](https://picsum.photos/seed/frontend/600/300)
![Backend flow](https://picsum.photos/seed/backend/600/300)

## Video and Audio

Markdown syntax for video and audio files:

Source:

```markdown
![Sample video](https://www.w3schools.com/tags/mov_bbb.mp4)

![Sample audio](https://www.learningcontainer.com/wp-content/uploads/2020/02/Kalimba.mp3)
```

Result:

![Sample video](https://www.w3schools.com/tags/mov_bbb.mp4)

![Sample audio](https://www.learningcontainer.com/wp-content/uploads/2020/02/Kalimba.mp3)

## HTML Media Tags

HTML media tags are recognized and converted to their respective media types.

Source:

```html
<img src="https://picsum.photos/seed/htmlmedia/800/400" alt="System diagram" />

<video src="https://www.w3schools.com/tags/mov_bbb.mp4"></video>

<audio src="https://www.learningcontainer.com/wp-content/uploads/2020/02/Kalimba.mp3"></audio>
```

Result:

<img src="https://picsum.photos/seed/htmlmedia/800/400" alt="System diagram" />

<video src="https://www.w3schools.com/tags/mov_bbb.mp4"></video>

<audio src="https://www.learningcontainer.com/wp-content/uploads/2020/02/Kalimba.mp3"></audio>

## HTML Anchor Tags

HTML anchors are converted to standard links.

Source:

```html
<a href="https://example.com/docs">Read the full documentation</a>
```

Result:

<a href="https://example.com/docs">Read the full documentation</a>

## Admonitions

### Standard Admonitions

!!! note "A Note"
    This is a standard note admonition. Use it for supplementary information
    that adds context without being critical to understanding.

!!! warning "Breaking Change"
    This API endpoint will be deprecated in v3.0. Migrate to the new
    `/api/v2/resources` endpoint before the next major release.

!!! tip "Pro Tip"
    You can chain multiple API calls using the batch endpoint to reduce
    round trips and improve performance.

!!! danger "Security Warning"
    Never commit API keys or secrets to version control. Use environment
    variables or a secrets manager instead.

### Collapsible Admonitions

Collapsed by default:

??? note "Click to expand details"
    This content is hidden by default. Users can expand it to see
    additional details about the topic.

Expanded by default:

???+ tip "Expanded by default"
    This collapsible section starts expanded. Users can collapse it
    if they want to hide it.

### GitHub GFM Callouts

Source:

```markdown
> [!NOTE]
> GFM-style callouts are automatically converted.

> [!TIP]
> Use GFM callouts when writing content in GitHub repositories.

> [!WARNING]
> This format is recognized and transformed during ingestion.

> [!CAUTION]
> Exercise caution when modifying production configuration.

> [!IMPORTANT]
> All team members must complete security training.
```

Result:

> [!NOTE]
> GFM-style callouts are automatically converted.

> [!TIP]
> Use GFM callouts when writing content in GitHub repositories.

> [!WARNING]
> This format is recognized and transformed during ingestion.

> [!CAUTION]
> Exercise caution when modifying production configuration.

> [!IMPORTANT]
> All team members must complete security training.

### Docusaurus Admonitions

Source:

```markdown
:::note
Docusaurus-style admonitions use triple-colon fences.
:::

:::tip
Tips provide helpful suggestions for developers.
:::

:::warning Custom Warning Title
Warnings with custom titles are supported.
:::

:::danger
Critical information about data loss or security.
:::

:::info
Informational callouts for general context.
:::

:::caution
Proceed carefully with shared infrastructure.
:::
```

Result:

:::note
Docusaurus-style admonitions use triple-colon fences.
:::

:::tip
Tips provide helpful suggestions for developers.
:::

:::warning Custom Warning Title
Warnings with custom titles are supported.
:::

:::danger
Critical information about data loss or security.
:::

:::info
Informational callouts for general context.
:::

:::caution
Proceed carefully with shared infrastructure.
:::

### Mintlify Admonitions

Source:

```markdown
<Note>Mintlify-style JSX admonitions are transformed into the standard format.</Note>

<Warning>Database migrations are irreversible. Always back up first.</Warning>

<Info>The platform supports up to 100 concurrent connections per tenant.</Info>

<Tip>Enable debug logging with LOG_LEVEL=debug for detailed traces.</Tip>

<Check>Your environment is correctly configured. All health checks passing.</Check>

<Caution>Rate limiting is enforced at 1000 requests per minute per API key.</Caution>
```

Result:

<Note>Mintlify-style JSX admonitions are transformed into the standard format.</Note>

<Warning>Database migrations are irreversible. Always back up first.</Warning>

<Info>The platform supports up to 100 concurrent connections per tenant.</Info>

<Tip>Enable debug logging with LOG_LEVEL=debug for detailed traces.</Tip>

<Check>Your environment is correctly configured. All health checks passing.</Check>

<Caution>Rate limiting is enforced at 1000 requests per minute per API key.</Caution>

## Tab Groups

### Standard Tabs

Source:

````markdown
!!! tabs
    - **JavaScript**
      ```js
      const response = await fetch('/api/data');
      const data = await response.json();
      console.log(data);
      ```
    - **Python**
      ```python
      import requests
      response = requests.get('/api/data')
      data = response.json()
      print(data)
      ```
    - **cURL**
      ```bash
      curl -s https://api.example.com/data | jq .
      ```
````

Result:

!!! tabs
    - **JavaScript**
      ```js
      const response = await fetch('/api/data');
      const data = await response.json();
      console.log(data);
      ```
    - **Python**
      ```python
      import requests
      response = requests.get('/api/data')
      data = response.json()
      print(data)
      ```
    - **cURL**
      ```bash
      curl -s https://api.example.com/data | jq .
      ```

### Docusaurus Tabs

Source:

````markdown
<Tabs>
  <TabItem label="npm">

```bash
npm install @acme/sdk
```

  </TabItem>
  <TabItem label="yarn">

```bash
yarn add @acme/sdk
```

  </TabItem>
  <TabItem label="pnpm">

```bash
pnpm add @acme/sdk
```

  </TabItem>
</Tabs>
````

Result:

<Tabs>
  <TabItem label="npm">

```bash
npm install @acme/sdk
```

  </TabItem>
  <TabItem label="yarn">

```bash
yarn add @acme/sdk
```

  </TabItem>
  <TabItem label="pnpm">

```bash
pnpm add @acme/sdk
```

  </TabItem>
</Tabs>

### Mintlify CodeGroup

Source:

````markdown
<CodeGroup>
```js server.js
const express = require('express');
const app = express();

app.get('/health', (req, res) => {
  res.json({ status: 'healthy' });
});

app.listen(3000);
```
```python server.py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/health')
def health():
    return jsonify(status='healthy')

if __name__ == '__main__':
    app.run(port=3000)
```
</CodeGroup>
````

Result:

<CodeGroup>
```js server.js
const express = require('express');
const app = express();

app.get('/health', (req, res) => {
  res.json({ status: 'healthy' });
});

app.listen(3000);
```
```python server.py
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/health')
def health():
    return jsonify(status='healthy')

if __name__ == '__main__':
    app.run(port=3000)
```
</CodeGroup>

## Steps

Source:

```markdown
<Steps>
  <Step title="Create an account">
    Sign up at the developer portal with your company email.
    You will receive a verification link within five minutes.
  </Step>
  <Step title="Generate API credentials">
    Navigate to Settings > API Keys and create a new key pair.
    Store the secret key securely — it is only shown once.
  </Step>
  <Step title="Make your first request">
    Use the credentials to authenticate and call the API.
  </Step>
</Steps>
```

Result:

<Steps>
  <Step title="Create an account">
    Sign up at the developer portal with your company email.
    You will receive a verification link within five minutes.
  </Step>
  <Step title="Generate API credentials">
    Navigate to Settings > API Keys and create a new key pair.
    Store the secret key securely — it is only shown once.
  </Step>
  <Step title="Make your first request">
    Use the credentials to authenticate and call the API.
  </Step>
</Steps>

## Cards

Source:

```markdown
<CardGroup>
<Card title="Quick Start Guide" href="getting-started">Get up and running in under five minutes.</Card>
<Card title="API Reference" href="https://api.example.com/docs">Complete endpoint documentation with examples.</Card>
<Card title="Architecture" href="architecture/overview">Understand how the system is structured.</Card>
</CardGroup>
```

Result:

<CardGroup>
<Card title="Quick Start Guide" href="getting-started">Get up and running in under five minutes.</Card>
<Card title="API Reference" href="https://api.example.com/docs">Complete endpoint documentation with examples.</Card>
<Card title="Architecture" href="architecture/overview">Understand how the system is structured.</Card>
</CardGroup>

## Accordion

Source:

```markdown
<Accordion title="What authentication methods are supported?">
The platform supports OAuth 2.0 with OIDC, API key authentication, and SAML SSO for enterprise accounts. See the Authentication Guide for details.
</Accordion>

<Accordion title="How do I reset my API key?">
Navigate to Settings > API Keys, revoke the existing key, and generate a new one. The old key is invalidated immediately.
</Accordion>
```

Result:

<Accordion title="What authentication methods are supported?">
The platform supports OAuth 2.0 with OIDC, API key authentication, and SAML SSO for enterprise accounts. See the Authentication Guide for details.
</Accordion>

<Accordion title="How do I reset my API key?">
Navigate to Settings > API Keys, revoke the existing key, and generate a new one. The old key is invalidated immediately.
</Accordion>

## Expandable

Source:

```markdown
<Expandable title="Advanced configuration options">
You can customize connection pooling, timeout values, and retry policies
through environment variables. See the deployment guide for the full list
of supported configuration parameters.
</Expandable>
```

Result:

<Expandable title="Advanced configuration options">
You can customize connection pooling, timeout values, and retry policies
through environment variables. See the deployment guide for the full list
of supported configuration parameters.
</Expandable>

## Collapsible HTML Sections

Source:

```markdown
<details>
<summary>View the full error log</summary>

2025-06-15T10:23:45Z ERROR [auth-service] Token validation failed
  cause: JWT signature mismatch
  tokenId: tok_abc123

</details>
```

Result:

<details>
<summary>View the full error log</summary>

2025-06-15T10:23:45Z ERROR [auth-service] Token validation failed
  cause: JWT signature mismatch
  tokenId: tok_abc123

</details>

## Internal Links

Links to other pages within the same module use relative paths:

- Sibling link: [Authentication Guide](authentication)
- Cross-group link: [Architecture Overview](../architecture/overview)
- Root-relative link: [Getting Started](../getting-started)

## Math

Inline math like $E = mc^2$ and block math are supported:

$$
\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n
$$

## Related Topics

For deployment and CI/CD configuration, see [Deployment](../architecture/deployment). For monitoring and observability, see [Monitoring](monitoring).
