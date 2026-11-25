# Perplexity Explorer

A single-page app that shows how surprised a real language model is by a sentence.
It runs **entirely in the browser** with [Transformers.js](https://huggingface.co/docs/transformers.js) and the `Xenova/distilgpt2` model.

- No build step, no framework, no backend, no API key, no environment variables.
- The model files (about 80 MB) are downloaded from Hugging Face the first time you click **Calculate perplexity**, then cached by the browser.

## Files

| File          | What it is                                                        |
| ------------- | ----------------------------------------------------------------- |
| `index.html`  | The whole app (HTML, CSS and JavaScript in one file)              |
| `vercel.json` | Vercel settings: clean URLs and a few safe security headers       |
| `.gitignore`  | Keeps `.vercel`, `node_modules`, `.env*` and `.DS_Store` out of git |

## Deploy on Vercel

1. Push this folder to a new GitHub, GitLab or Bitbucket repository:

   ```bash
   git init
   git add .
   git commit -m "Perplexity Explorer"
   git branch -M main
   git remote add origin https://github.com/<your-name>/<your-repo>.git
   git push -u origin main
   ```

2. Go to <https://vercel.com/new> and import the repository.
3. Leave the settings as they are:
   - Framework Preset: **Other**
   - Build Command: empty
   - Output Directory: empty
   - Root Directory: `./`
4. Click **Deploy**. Every later `git push` redeploys automatically.

Prefer the command line? Run `npm i -g vercel`, then `vercel` for a preview deploy or `vercel --prod` for production.

## Run it locally

Serve the folder over http (opening the file directly can block the model download):

```bash
python3 -m http.server 3000
# then open http://localhost:3000
```

## Notes

- Do not add a strict `Content-Security-Policy` header without allowing `cdn.jsdelivr.net`, `huggingface.co` (and its download hosts), `blob:` and `'wasm-unsafe-eval'`. Otherwise the model cannot load.
- If the model fails to load, the page shows a red error message. Check the internet connection, then try again.
# perplexity-llm
