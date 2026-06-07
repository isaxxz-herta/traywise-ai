# TrayWise AI

An intelligent image analysis application that uses AWS Rekognition to identify and analyze objects in images. Built as a full-stack monorepo with a modern React frontend and Flask backend.

## 🎯 Features

- **Image Upload & Analysis**: Upload images for real-time object detection and labeling
- **AWS Rekognition Integration**: Leverages AWS AI services for accurate object recognition
- **Modern UI**: Built with React and Radix UI components with Tailwind CSS styling
- **Responsive Design**: Works seamlessly across devices
- **Cloud Storage**: Automatic S3 integration for image storage and retrieval
- **Real-time Results**: View analysis results instantly

## 📁 Project Structure

```
traywise-ai/
├── backend/                    # Flask application
│   ├── application.py          # Main Flask app with AWS Rekognition integration
│   ├── requirements.txt         # Python dependencies
│   ├── Procfile                # Elastic Beanstalk deployment config
│   ├── static/                 # Static assets
│   └── templates/              # HTML templates
├── frontend/                   # React application
│   ├── src/
│   │   ├── components/         # React components
│   │   │   ├── ui/            # Radix UI component library
│   │   │   ├── CameraPage.tsx
│   │   │   ├── FinishPage.tsx
│   │   │   ├── LandingPage.tsx
│   │   │   └── ResultsPage.tsx
│   │   ├── styles/            # Global styles
│   │   ├── App.tsx            # Main app component
│   │   └── main.tsx           # React entry point
│   ├── package.json           # Node dependencies
│   ├── vite.config.ts         # Vite configuration
│   └── index.html             # HTML entry point
├── README.md                  # This file
└── .gitignore

```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+ (for frontend)
- Python 3.9+ (for backend)
- AWS Account with Rekognition and S3 access
- pip and npm package managers

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
# Create a .env file with:
# INPUT_BUCKET=your-input-bucket
# OUTPUT_BUCKET=your-output-bucket
# AWS_DEFAULT_REGION=us-east-1
# REK_MAX_LABELS=10
# REK_MIN_CONFIDENCE=50

# Run the Flask application
python -m flask run
# Or for production:
gunicorn -b 0.0.0.0:5000 application:application
```

### Frontend Setup

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

## 🌐 Environment Variables

### Backend (Flask)

| Variable | Default | Description |
|----------|---------|-------------|
| `INPUT_BUCKET` | `traywise-videos` | S3 bucket for input images |
| `OUTPUT_BUCKET` | `traywise-outputs` | S3 bucket for output results |
| `AWS_DEFAULT_REGION` | `us-east-1` | AWS region |
| `REK_MAX_LABELS` | `10` | Max labels from Rekognition |
| `REK_MIN_CONFIDENCE` | `50` | Confidence threshold (0-100) |

### Frontend

Configure API endpoint in `frontend/src/` files to point to your backend URL.

## 📦 Dependencies

### Backend

- **Flask**: Web framework
- **boto3**: AWS SDK for Rekognition and S3
- **Pillow**: Image processing
- **OpenCV**: Computer vision operations
- **gunicorn**: Production WSGI server

### Frontend

- **React 18**: UI framework
- **Vite**: Build tool
- **Radix UI**: Component library
- **Tailwind CSS**: Utility-first CSS
- **React Hook Form**: Form handling
- **Recharts**: Data visualization

## 🚢 Deployment

### Backend (AWS Elastic Beanstalk)

The `Procfile` is pre-configured for EB deployment:

```bash
# Deploy with EB CLI
eb init
eb create traywise-env
eb deploy
```

### Frontend (Static Hosting)

Build and deploy to services like Vercel, Netlify, or AWS S3 + CloudFront:

```bash
cd frontend
npm run build
# Deploy the dist/ folder
```

## 🔑 API Endpoints

### POST /upload
Upload an image for analysis
- **Body**: FormData with image file
- **Response**: JSON with analysis results

### GET /results/<file_id>
Retrieve stored analysis results
- **Response**: JSON with detected labels and confidence scores

## 🛠️ Development

### Code Structure

- **Backend**: Single Flask app (`application.py`) handling all routes
- **Frontend**: Component-based React architecture with page components and reusable UI components

### Testing

```bash
# Backend: Add tests in a tests/ directory
pytest tests/

# Frontend: Run tests with Vitest
npm run test
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project was created for a hackathon. Check LICENSE file for details.

## 👨‍💻 Author

Created as a hackathon project - First full-stack application with AI integration!

---

**Last Updated**: June 2026
