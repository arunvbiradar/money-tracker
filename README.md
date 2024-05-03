# Money Tracker

## Commands

- npx create-next-app@latest .
- npm i @clerk/nextjs
- npx shadcn-ui@latest init
- npx shadcn-ui@latest add
- npm i next-themes

## Steps

### 1. logged in to clerk website

### 2. .env.local

```bash
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=publish_key
CLERK_SECRET_KEY=secret_key
```

### 3. clerk code

```typescript
import { ClerkProvider } from "@clerk/nextjs";
export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <ClerkProvider>
      <html lang="en">
        <body>{children}</body>
      </html>
    </ClerkProvider>
  );
}
```

### 4. ./middleware.ts

```typescript
import { clerkMiddleware } from "@clerk/nextjs/server";

export default clerkMiddleware();

export const config = {
  matcher: ["/((?!.+.[w]+$|_next).*)", "/", "/(api|trpc)(.*)"],
};
```

### 5. ./app/(auth)/layout.tsx

### 6. ./app/(auth)/sign-up/[[...sign-up]]/page.tsx

```typescript
import { SignUp } from "@clerk/nextjs";

export default function Page() {
  return <SignUp path="/sign-up" />;
}
```

### 7. ./app/(auth)/sign-in/[[...sign-in]]/page.tsx

```typescript
import { SignIn } from "@clerk/nextjs";

export default function Page() {
  return <SignIn path="/sign-in" />;
}
```

### 8. add public sign-in, sign-up

```bash
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/wizard
```

### 9. shadcn install

### 10. npm i next-themes
