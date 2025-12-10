# Architecture Overview

## Data Flow

1.  **User Upload**: User drags & drops images into the Dashboard (`/dashboard`).
2.  **Storage**: Images are uploaded to Supabase Storage bucket `bizcards`.
3.  **Trigger/Process**:
    *   *Option A (Client-side trigger)*: Client calls Next.js API route `/api/process-card` with the image URL.
    *   *Option B (Async)*: Supabase Edge Function listens to `INSERT` on storage (advanced).
    *   *We are using Option A for simplicity.*
4.  **AI Analysis**:
    *   Server reads image buffer.
    *   Sends to **Gemini Pro Vision** with a structured prompt: "Extract business card details in JSON format..."
5.  **Database**:
    *   Parsed JSON is validated.
    *   Record created in `cards` table with status `reviewed: false`.
6.  **UI Update**: Realtime subscription or optimistic UI updates the dashboard list.

## Database Schema (Supabase)

### `profiles`
- `id`: uuid (references auth.users)
- `full_name`: text
- `avatar_url`: text

### `cards`
- `id`: uuid
- `user_id`: uuid (references profiles.id)
- `image_url`: text
- `name`: text
- `title`: text
- `company`: text
- `email`: text
- `phone`: text
- `website`: text
- `address`: text
- `meta_data`: jsonb (AI confidence scores, raw response)
- `created_at`: timestamp
