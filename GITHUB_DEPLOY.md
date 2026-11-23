# GitHub + deployment (beginner guide)

## Upload the project to GitHub
1. Sign in to GitHub and create a new repository named `armory-3d`.
2. Keep the repository empty (do not add a README, license, or .gitignore; the project already has these files).
3. Download this project ZIP and extract it on your computer.
4. Upload the **contents** of the `armory-3d` folder to the repository (not the enclosing folder). On GitHub's web interface, use **Add file → Upload files**.
5. Commit the upload.

## Publish it with Vercel
1. Open Vercel and sign in with GitHub.
2. Add a new project and import `armory-3d`.
3. Keep the build command `npm run build` and output directory `dist` (the included `vercel.json` also configures this).
4. Deploy. Vercel will provide a public URL, usable on phones.

## Notes
- A real GLB model is not included in this archive. The 3D objects are proxy models made from shapes.
- The current catalog contains three quadcopters and placeholder categories.
- The build workflow in `.github/workflows/build.yml` checks that the project builds after commits and pull requests.
