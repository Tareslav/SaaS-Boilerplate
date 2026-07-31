## **Status**

Initial technical foundation. Product-specific architecture is not approved yet.

## **Current stack**

Verify every item against the repository before relying on this list:

* Framework: Next.js  
* Language: TypeScript  
* Authentication: Clerk  
* Database: Neon/PostgreSQL  
* Hosting: Vercel  
* Version control: GitHub

## **Environments**

* Local development  
* Vercel preview  
* Production

Production changes require explicit user approval.

## **Current components**

TBD after repository inspection.

## **Data model**

No product-specific data model is approved.

## **Authentication**

Clerk is expected to handle authentication.

Authorization rules must be designed after the product, roles, resource ownership, and guest-access requirements are defined.

## **External services**

Do not add external services without approval.

## **Architecture principles**

1. Prefer the existing stack.  
2. Keep the MVP small.  
3. Avoid premature abstraction.  
4. Prefer reversible decisions.  
5. Prefer additive database migrations.  
6. Validate authorization server-side.  
7. Never expose secrets to the client.  
8. Use preview environments before production.

