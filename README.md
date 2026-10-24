# LifeFlow mobile

Arabic local-first personal organizer. Open the deployed page in Safari or Chrome, then add it to the Home Screen. Records remain in this browser's IndexedDB. No desktop computer, LAN service, cloud database or external AI is required for normal use. Cross-device sync is not enabled.

This repository contains the production build. Editable source is in lifeflow-source.zip. Install dependencies with pnpm install --frozen-lockfile. Build with LIFEFLOW_BASE_PATH=/lifeflow/ and pnpm build. Use GitHub Pages: deploy from branch main, root folder.

The initial online visit downloads app assets. Actual installed iPhone offline behavior still needs device verification. Export JSON backups from settings; clearing site data can remove local records.

Automated rules suite: 234 passing cases. Deployment package includes no user records, credentials, backups, or test database. Asset attributions: ASSET-LICENSES.md.
