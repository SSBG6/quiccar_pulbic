# Quiccar

Quiccar is a Node.js web application (Express + EJS + MongoDB) with an integrated Python/YOLOv5 vehicle detection component, used to identify and classify vehicles (e.g. bikes, cars, three-wheelers) from uploaded images.

> ⚠️ This is a public copy of the project (`quiccar_public`). Fill in or adjust any sections below marked with `TODO` to match the actual intended use case, deployment, and license.

---

## Features

- **Web app backend** — Express server (`index.js`) rendering server-side views with EJS
- **User accounts & auth** — session-based login (`express-session`, `connect-mongo`) with password hashing (`bcrypt` / `bcryptjs`) and JWT support
- **Data storage** — MongoDB via Mongoose
- **File & image uploads** — handled with `multer`, processed with `sharp`
- **Cloud storage** — supports both Google Cloud Storage and AWS S3
- **Email notifications** — via `nodemailer`
- **Vehicle image detection** — Python scripts using YOLOv5 (`yolov5s.pt`, `best.pt`, `last.pt`) to detect and classify vehicles from photos
- **Form validation** — `express-validator`

## Tech Stack

| Layer            | Technology                              |
|-------------------|------------------------------------------|
| Backend           | Node.js, Express                        |
| Views             | EJS, Bootstrap 5                        |
| Database          | MongoDB (Mongoose)                      |
| Auth              | express-session, bcrypt/bcryptjs, JWT   |
| Storage           | Google Cloud Storage, AWS S3            |
| Image processing  | Sharp                                   |
| ML / vision       | Python, YOLOv5, OpenCV (assumed)        |
| Email             | Nodemailer                              |

## Project Structure

```
quiccar_public/
├── controllers/       # Express route handlers / business logic
├── js/                 # Client-side JavaScript
├── models/             # Mongoose schemas
├── public/              # Static assets served by Express
├── uploads/             # Uploaded image storage
├── views/               # EJS templates
├── index.js             # Application entry point
├── des.py, ip.py, ip2.py, test*.py, title.py   # Python scripts for vehicle
│                                                  detection / image processing
├── best.pt, last.pt, yolov5s.pt                  # YOLOv5 model weights
├── package.json
└── package-lock.json
```

> `TODO`: Add a short description of what each Python script does (`des.py`, `ip.py`, `ip2.py`, `test.py`, `test2.py`, `test3.py`, `title.py`) — e.g. detection, cropping, plate/title recognition, etc.

## Getting Started

### Prerequisites

- Node.js (LTS recommended) and npm
- MongoDB instance (local or hosted, e.g. MongoDB Atlas)
- Python 3.x with `pip`, if you plan to run the vehicle-detection scripts
- Google Cloud Storage and/or AWS S3 credentials, if using cloud uploads

### Installation

```bash
git clone https://github.com/SSBG6/quiccar_public.git
cd quiccar_public
npm install
```

For the Python/YOLOv5 components:

```bash
pip install -r requirements.txt   # TODO: add a requirements.txt if not already present
```

### Environment Variables

Create a `.env` file in the project root. At minimum you'll likely need:

```env
MONGODB_URI=
SESSION_SECRET=
JWT_SECRET=

# Google Cloud Storage
GCS_BUCKET_NAME=
GOOGLE_APPLICATION_CREDENTIALS=

# AWS S3
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_S3_BUCKET=

# Email
SMTP_HOST=
SMTP_USER=
SMTP_PASS=
```

> `TODO`: Confirm the exact variable names expected by `index.js` and the files in `controllers/`, and update this list accordingly.

### Running the App

```bash
npm start
```

This runs `nodemon index.js`, so the server restarts automatically on file changes during development.

## Vehicle Detection (Python)

The repo includes pretrained YOLOv5 weights (`yolov5s.pt`, `best.pt`, `last.pt`) along with sample images (`bike.jpg`, `bikew.jpg`, `honda.jpg`, `threewheeler.jpeg`) used to detect and classify vehicle types from photos, likely for listing verification or categorization within the app.

```bash
python des.py   # TODO: confirm actual usage/entry point for detection
```

> `TODO`: Document how the Node app and the Python detection scripts communicate (e.g. child process call, REST API, message queue) — this isn't obvious from the file layout alone.

## Contributing

Pull requests are welcome. For significant changes, please open an issue first to discuss what you'd like to change.

## License

`TODO`: No license is currently specified in `package.json`. Add a `LICENSE` file and update this section (e.g. MIT, ISC) if this project is intended to be open source.
