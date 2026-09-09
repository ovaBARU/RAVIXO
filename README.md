# RAVIXO — GitHub + Railway Ready

RAVIXO is a single-service Express + PostgreSQL social-media application.

## Railway

1. Upload the CONTENT of this folder to the root of a new GitHub repository. Do not put it inside another `RAVIXO/` subfolder.
2. In Railway, connect that GitHub repository as the RAVIXO service.
3. Add a PostgreSQL service to the same Railway project.
4. Ensure the RAVIXO service receives `DATABASE_URL` from PostgreSQL.
5. Add `JWT_SECRET` with a long random secret.
6. Set the service Start Command to `npm start` (or leave the included `railway.toml` in the repository).
7. Deploy. The app runs the database migration first, then starts Express.
8. Open `/health`; a healthy service returns JSON with `ok: true`.

## Important

Do not merge this project with an older repository that has a different `package.json`, `src/`, `database/`, `scripts/`, or a start command such as `npm run migrate` unless you intentionally merge them. The previous Railway error `npm error Missing script: "migrate"` means Railway was executing a `migrate` script that did not exist in the deployed package.json.

## Local

```bash
npm install
npm start
```

Environment variables:
- `DATABASE_URL` — PostgreSQL connection string
- `JWT_SECRET` — required secret for JWT signing
- `PORT` — optional; Railway provides it automatically

## Media

Uploaded media is stored under `uploads/`. Railway service storage can be ephemeral, so production deployments should eventually move media to object storage such as S3/R2/Supabase Storage.
