# Builder Domains

> Free domain names for builders and AI agents

Builder Domains provides instant, free domain names so you can launch projects without registration friction, DNS complexity, or renewal headaches.

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    builder.domains                           │
├─────────────────────────────────────────────────────────────┤
│  Claim → Configure → Connect → Ship                         │
│                                                             │
│  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐    │
│  │ Instant │   │  Auto   │   │   DNS   │   │Redirect │    │
│  │  Claim  │   │   SSL   │   │  Mgmt   │   │  Rules  │    │
│  └─────────┘   └─────────┘   └─────────┘   └─────────┘    │
│  ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐    │
│  │Wildcard │   │Analytics│   │ Upgrade │   │   API   │    │
│  │ Support │   │         │   │  Path   │   │  First  │    │
│  └─────────┘   └─────────┘   └─────────┘   └─────────┘    │
├─────────────────────────────────────────────────────────────┤
│              api.builder.domains  ←→  db.builder.domains    │
└─────────────────────────────────────────────────────────────┘
```

## Installation

```bash
npm install builder.domains
```

## Quick Start

```typescript
import { Domain } from 'builder.domains'

// Claim a domain instantly
const domain = await Domain.claim({
  name: 'myproject',
  tld: 'build'
})

// Connect to your deployment
await domain.connect({
  target: 'my-project.vercel.app'
})

console.log(domain.url)  // https://myproject.build
```

## CLI Usage

```bash
# Claim a domain
npx builder.domains claim myproject

# Check availability
npx builder.domains check myproject

# Connect to deployment
npx builder.domains connect myproject.build --target my-project.vercel.app

# List your domains
npx builder.domains list
```

## Available TLDs

| TLD | Use Case | Example |
|-----|----------|---------|
| `.build` | General projects | `myapp.build` |
| `.dev.build` | Development/staging | `myapp.dev.build` |
| `.demo.build` | Demos and prototypes | `myapp.demo.build` |
| `.api.build` | API endpoints | `myapp.api.build` |
| `.app.build` | Applications | `myapp.app.build` |
| `.ai.build` | AI projects | `myapp.ai.build` |

## Features

### Instant Claim

No registration flow. No email verification. No credit card.

```typescript
const domain = await Domain.claim({
  name: 'myproject'
})
// Domain is live in < 1 second
```

### Automatic SSL

HTTPS enabled automatically. No certificate management required.

```typescript
const domain = await Domain.claim({
  name: 'myproject',
  ssl: true  // Default: true
})

console.log(domain.url)  // https://myproject.build
```

### DNS Management

Simple API for DNS records when you need them.

```typescript
await domain.dns.add({
  type: 'CNAME',
  name: 'www',
  value: 'myproject.build'
})

await domain.dns.add({
  type: 'TXT',
  name: '_verify',
  value: 'verification-token'
})
```

### Wildcard Support

Enable wildcard subdomains for multi-tenant apps.

```typescript
await domain.enableWildcard()

// Now *.myproject.build resolves
// customer1.myproject.build
// customer2.myproject.build
```

### Redirects

Set up URL forwarding and redirects.

```typescript
await domain.redirect({
  from: 'old.myproject.build',
  to: 'new.myproject.build',
  type: 301
})
```

### Analytics

Basic traffic analytics included.

```typescript
const stats = await domain.analytics({
  period: 'last-7-days'
})

console.log(stats.visitors)
console.log(stats.pageviews)
console.log(stats.countries)
```

## Integration with Deployments

### Vercel

```typescript
await domain.connect({
  provider: 'vercel',
  project: 'my-project'
})
```

### Netlify

```typescript
await domain.connect({
  provider: 'netlify',
  site: 'my-site'
})
```

### Railway

```typescript
await domain.connect({
  provider: 'railway',
  service: 'my-service'
})
```

### Custom Target

```typescript
await domain.connect({
  target: '123.456.789.0',
  type: 'A'
})

// Or CNAME
await domain.connect({
  target: 'my-app.herokuapp.com',
  type: 'CNAME'
})
```

## AI Agent Usage

Perfect for autonomous startup creation:

```typescript
import { Domain } from 'builder.domains'
import { Startup } from 'startup-builder'

// AI agent creates a startup
const startup = await Startup.create({
  name: 'NewIdea',
  icp: 'developers'
})

// Automatically provision domains
const domains = await Domain.claimForStartup(startup, {
  tlds: ['build', 'api.build', 'app.build']
})

// domains.site = https://newidea.build
// domains.api = https://newidea.api.build
// domains.app = https://newidea.app.build
```

## Upgrade Path

Ready for production? Upgrade to a custom domain.

```typescript
// Check if a custom domain is available
const available = await Domain.checkCustom('myproject.com')

// Purchase and migrate
if (available) {
  await domain.upgrade({
    target: 'myproject.com',
    provider: 'namecheap',  // or cloudflare, google, etc.
    migrate: true           // Move DNS settings
  })
}
```

## Configuration

```typescript
// domains.config.ts
import { defineConfig } from 'builder.domains'

export default defineConfig({
  defaults: {
    ssl: true,
    analytics: true
  },
  organization: {
    id: process.env.ORG_ID,
    plan: 'studio'
  }
})
```

## Related Packages

| Package | Description |
|---------|-------------|
| [startup-builder](https://npmjs.com/package/startup-builder) | Build autonomous startups |
| [sales-builder](https://npmjs.com/package/sales-builder) | Autonomous sales workflows |
| [service-builder](https://npmjs.com/package/service-builder) | AI-delivered Services-as-Software |
| [startup.games](https://npmjs.com/package/startup.games) | Gamification for founders |

## License

MIT
