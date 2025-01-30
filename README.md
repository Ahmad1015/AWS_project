# File Sharing Service

## Overview  
This project is a secure file-sharing service inspired by Google Drive. It allows authenticated users to upload, manage, and share files with temporary access links. Built with **Node.js (Express.js)** for the backend, **MongoDB** for file metadata storage, and **AWS S3** for cloud file storage, this service ensures security, scalability, and efficiency.  

## Features  
### **1. User Authentication**  
- User registration with email and password (hashed using bcrypt).  
- JWT-based authentication with token expiration.  

### **2. File Upload**  
- Authenticated users can upload files.  
- Files are stored in AWS S3 in user-specific folders.  
- Enforced limits on file size (10MB) and supported file types (.pdf, .png, .jpg, .txt).  
- File metadata (name, size, upload date, S3 URL) is stored in MongoDB.  

### **3. File Management**  
- **Generate Temporary Links:** Users can create pre-signed URLs with time-limited access (e.g., 1 hour, 24 hours).  
- **File Access:** Only users with valid pre-signed URLs can access files.  
- **File Deletion:** Users can delete their uploaded files, removing them from both S3 and MongoDB.  
- **File List:** Users can view their uploaded files, including metadata and expiration times for shared links.  

### **4. Security & Error Handling**  
- Secure JWT authentication and input validation.  
- Pre-signed URLs for controlled file access.  
- Role-based access to prevent unauthorized actions.  
- Clear error messages with appropriate HTTP status codes (400, 401, 403, 404, 500).  

### **5. Analytics Dashboard**  
- Displays total files uploaded, storage used, and recent uploads.  

## Tech Stack  
- **Backend:** Node.js (Express.js)  
- **Database:** MongoDB  
- **Cloud Storage:** AWS S3  
- **Authentication:** JWT & bcrypt  

## AWS Features Used  
- **S3 Buckets:** For secure file storage.  
- **Pre-signed URLs:** For controlled file sharing.  
- **IAM Roles & Policies:** To restrict access securely.  

## API Endpoints  
| Endpoint | Method | Description | Authentication |  
|----------|--------|-------------|---------------|  
| `/auth/register` | POST | Register a new user | No |  
| `/auth/login` | POST | User login, returns JWT | No |  
| `/files/upload` | POST | Upload a file | Yes |  
| `/files/list` | GET | List user's files | Yes |  
| `/files/generate-link/:fileId` | GET | Generate pre-signed URL | Yes |  
| `/files/delete/:fileId` | DELETE | Delete a file | Yes |  

## Frontend  
- Built with **React.js** to integrate with backend APIs.  
- Simple UI for authentication, file uploads, and management.  

## Optional Enhancements  
- **Email notifications** (AWS SES) for file actions.  
- **Audit logs** for tracking file activities.  
- **Storage limits** per user.  
- **File encryption** before uploading.  
- **Rate limiting** to prevent abuse.  

## Installation & Setup  
1. Clone the repository:  
   ```sh
   git clone https://github.com/your-repo/file-sharing-service.git  
   cd file-sharing-service  
   ```  
2. Install dependencies in both Frontend and Backend:  
   ```sh
   npm install  
   ```  
3. Set up environment variables (`.env` file) for both frontend and backend:  
   
4. Start the server:  
   ```sh
   npm start  
   ```  

## License  
This project is licensed under the MIT License.  
