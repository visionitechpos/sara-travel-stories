# Assets

This folder contains all visual assets, character images, and project resources.

**Storage policy (since 2026-07-01):** Actual image and video files live in Google Drive (`visionitechpos@gmail.com`, root folder "Sara Travel Stories - Media"), mirroring this folder structure — see `episodes/PRODUCTION_DECISIONS_LOG.md` ("Media Storage Moved to Google Drive"). This repo keeps structure and documentation only.

---

## Folder Structure

```
assets/
  sara/
    [approved character reference images]
  locations/
    [produced location visuals]
  thumbnails/
    [episode thumbnail files]
  branding/
    [logos, brand marks, channel art]
```

---

## Sara Assets (LOCKED)

The `/sara/` subfolder corresponds to the Google Drive folder holding the approved character reference images.

**Sync status: complete (2026-07-01).** Primary reference: [sara-face-reference-approved-2026-07-01.jpeg](https://drive.google.com/file/d/1AiheN-J48AZ461S9PGVIb0hkrTlf9kLQ/view). Wardrobe references live in the `sara/wardrobe/` subfolder in Drive — see `prompts/character/sara_outfit_guide.md` Wardrobe Log.

These Drive files are the source of truth for Sara's visual identity.

**Rules:**
* Do not modify approved Sara images.
* Do not generate new Sara variants without explicit approval.
* If a new approved image is created, add it here with a clear filename and date.

### Filename Convention for Sara Assets

`sara-[description]-approved-[YYYY-MM-DD].[ext]`

Example:
* `sara-base-reference-approved-2026-06-21.jpg`

---

## Location Assets

The `/locations/` subfolder stores final produced location visuals used in episodes.

Organize by episode:
```
locations/
  ep001_al-balad-jeddah/
  ep002_.../
```

---

## Thumbnails

The `/thumbnails/` subfolder stores final episode thumbnails.

Filename: `ep[number]-thumbnail-v[version].[ext]`

Example: `ep001-thumbnail-v1.jpg`

---

## Branding

The `/branding/` subfolder stores channel art and brand assets.

Do not modify branding assets without explicit approval.
