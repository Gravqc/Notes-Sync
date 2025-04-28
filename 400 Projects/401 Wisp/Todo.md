
---
# Backend 

## 1. Authentication (Session + JWT)
- [x] Install `jsonwebtoken` and `cookie` libraries
- [x] Create JWT signing helper
- [x] Create JWT verification helper
- [x] Create middleware to protect private routes
- [x] Issue JWT on login and signup
- [x] Save JWT inside HttpOnly cookie
- [x] Implement `/api/me` route to get current user session
- [x] Protect post/comment creation routes using session

## 2. User Anonymity (Blind Style)
- [x] Create one-way hashing function for user identity (SHA-256)
- [ ] Hash user's email when creating a post
- [ ] Hash user's email when creating a comment
- [ ] Never expose real email/userId in post or comment APIs

## 3. Posts CRUD
- [ ] Create `Post` model
- [ ] Implement `POST /api/posts` (create post)
- [ ] Implement `GET /api/posts` (list posts, paginated)
- [ ] Implement `GET /api/posts/:id` (get single post)
- [ ] Implement `PATCH /api/posts/:id` (edit post - only author)
- [ ] Implement `DELETE /api/posts/:id` (delete post - only author)
- [ ] Protect create/edit/delete with session auth

## 4. Comments CRUD
- [ ] Create `Comment` model
- [ ] Implement `POST /api/posts/:id/comments` (create comment)
- [ ] Implement `GET /api/posts/:id/comments` (list comments)
- [ ] Implement `DELETE /api/comments/:id` (delete comment - only author)
- [ ] Protect comment creation/deletion with session auth

## 5. Votes System (Optional for later)
- [ ] Design Vote model (userId, targetId, type)
- [ ] Implement upvote/downvote API for posts
- [ ] Implement upvote/downvote API for comments
- [ ] Prevent double voting by same user

## 6. Organization Feeds (Optional later)
- [ ] Filter posts by user's organization (eg: show posts from same company or college)
- [ ] Create `/api/org-feed` endpoint

## 7. Security & Cleanup
- [ ] Validate all API inputs (use Zod or simple manual validation)
- [ ] Set CORS headers properly if needed
- [ ] Add basic rate limiting to sensitive APIs (signup, login)
- [ ] Add error handling middleware (500 errors)
## 8. Data Access Layer (DAL)
- [x] Create `/lib/services/UserService.ts`
- [x] Create `/lib/services/PostService.ts`
- [x] Create `/lib/services/CommentService.ts`
- [x] Refactor API routes to call service functions

## 9. Data Transfer Objects (DTOs)
- [x] Create `/lib/dtos/user.dto.ts`
- [x] Create `/lib/dtos/post.dto.ts`
- [x] Create `/lib/dtos/comment.dto.ts`
- [x] Enforce DTOs in API request/response handling


