# Copilot Instructions for baumannzinho-upload

## Overview
This monorepo contains two main projects:
- **frontend/**: Angular application for user interaction and file uploads.
- **upload/**: NestJS backend for file management and API services.

## Architecture & Data Flow
- The **frontend** (Angular) communicates with the **upload** (NestJS) backend via HTTP APIs for file upload and retrieval.
- Backend structure follows standard NestJS conventions: `controller`, `service`, `module`, `dto`, and `entity` layers. File upload logic is in `upload/src/arquivo/`.
- Frontend pages are organized under `src/app/pages/`, with upload logic in `src/app/pages/upload/`.

## Key Workflows
### Frontend (Angular)
- **Start dev server:** `npm start` or `ng serve` in `frontend/`
- **Build:** `npm run build` or `ng build`
- **Test:** `npm test` or `ng test`
- Main entry: `src/main.ts`, routes in `src/app/app.routes.ts`

### Backend (NestJS)
- **Start dev server:** `npm run start:dev` in `upload/`
- **Build:** `npm run build`
- **Test:** `npm test` (Jest)
- **Lint:** `npm run lint`
- **Format:** `npm run format`
- Main entry: `src/main.ts`, API routes in `src/arquivo/arquivo.controller.ts`

## Project-Specific Patterns
- **DTOs**: All request/response validation is handled via DTOs in `upload/src/arquivo/dto/`.
- **Entities**: Data models are in `upload/src/arquivo/entities/`.
- **Services**: Business logic is in `upload/src/arquivo/arquivo.service.ts`.
- **Frontend Services**: API calls are abstracted in `frontend/src/app/services/`.
- **Page Components**: Each page (e.g., upload) has its own folder with `.ts`, `.html`, `.css`, and `.spec.ts` files.

## Conventions
- Use Angular and NestJS CLI for generating new components/services/modules.
- Keep API contracts in sync between frontend and backend (update DTOs and service calls together).
- Use `test/` for backend e2e tests.
- Use `public/` in frontend for static assets.

## Integration Points
- **Frontend ↔ Backend**: All file upload/download actions go through the backend API defined in `arquivo.controller.ts`.
- **External dependencies**: Managed via `package.json` in each project. Use `npm install` in the respective folder.

## Examples
- To add a new upload feature:
  1. Add API in `arquivo.controller.ts` and logic in `arquivo.service.ts`.
  2. Update/create DTOs as needed.
  3. Add/modify Angular service in `frontend/src/app/services/`.
  4. Update UI in `frontend/src/app/pages/upload/`.

## References
- [frontend/README.md](../frontend/README.md)
- [upload/README.md](../upload/README.md)
- [NestJS Documentation](https://docs.nestjs.com)
- [Angular Documentation](https://angular.io/docs)

---
For any unclear or missing conventions, review the respective `README.md` or ask for clarification.
