# 🚗 RideFusion - Ride Sharing Platform

## 📋 Project Overview

**RideFusion** is a comprehensive ride-sharing platform built with **ASP.NET Core 8** that connects drivers and passengers for cost-effective, eco-friendly transportation. The platform enables users to offer rides as drivers or book rides as passengers, creating a community-driven transportation solution.

### 🎯 Purpose
- **Cost Reduction**: Split travel costs between multiple passengers
- **Environmental Impact**: Reduce carbon footprint through shared transportation
- **Community Building**: Connect people traveling similar routes
- **Convenience**: Easy-to-use platform for ride coordination

### 🛠️ Technology Stack
- **Backend**: ASP.NET Core 8.0 (MVC Pattern)
- **Language**: C# 12.0
- **Database**: SQLite with Entity Framework Core 8.0
- **Authentication**: ASP.NET Core Identity
- **Frontend**: Razor Pages + Bootstrap 5
- **Icons**: Font Awesome
- **JavaScript**: jQuery + Bootstrap JS

---

## ✨ Features Implemented

### 🔐 Authentication & Authorization
- **User Registration**: Role-based registration (Driver/Passenger)
- **Secure Login**: ASP.NET Core Identity with cookie authentication
- **Role Management**: Separate access controls for drivers and passengers
- **Profile Validation**: Mandatory profile completion before using core features

### 👤 User Management
- **Comprehensive Profiles**: Personal information, contact details
- **Driver-Specific Fields**: Vehicle details, license information, UPI payment ID
- **Profile Completion Enforcement**: Custom filter ensures required fields are filled
- **Account Security**: Password hashing, secure session management

### 🚗 Ride Management (Driver Features)
- **Create Rides**: Post ride offers with route, timing, and pricing
- **Manage Rides**: Edit, delete, and view ride details
- **Passenger Management**: View and manage bookings for each ride
- **Real-time Availability**: Automatic seat count updates
- **Future Date Validation**: Custom validation to prevent past date entries

### 🔍 Ride Discovery (Passenger Features)
- **Advanced Search**: Filter rides by location, date, and availability
- **Detailed View**: Complete ride information including driver details
- **Instant Booking**: No approval needed - immediate confirmation
- **Booking Management**: View, track, and cancel bookings

### 📱 User Interface
- **Responsive Design**: Mobile-first approach with Bootstrap 5
- **Intuitive Navigation**: Role-based menu system
- **Real-time Feedback**: Success/error messages with TempData
- **Clean Layout**: Modern card-based design with professional styling

### 🛡️ Security Features
- **CSRF Protection**: ValidateAntiForgeryToken on all POST actions
- **Input Validation**: Data annotations and custom validators
- **Authorization Filters**: Role-based and profile-completion checks
- **Secure Data Access**: Users can only access their own data

### 📊 Data Management
- **Database Relationships**: Proper foreign key constraints
- **Migration System**: Version-controlled database schema
- **Data Integrity**: Cascade delete rules and referential integrity
- **Optimized Queries**: Include statements for efficient data loading

---

## 🚀 Setup Instructions (How to Run)

### Prerequisites
- **.NET 8.0 SDK** - [Download here](https://dotnet.microsoft.com/download/dotnet/8.0)
- **Visual Studio 2022** or **VS Code** with C# extension
- **Git** for version control

### Step 1: Clone the Repository
```bash
git clone https://github.com/yagnik1505/RideFusion.git
cd RideFusion
```

### Step 2: Restore Dependencies
```bash
dotnet restore
```

### Step 3: Setup Database
```bash
# Apply database migrations
dotnet ef database update

# This will create SQLite database with all required tables
```

### Step 4: Build the Project
```bash
dotnet build
```

### Step 5: Run the Application
```bash
dotnet run
```

### Step 6: Access the Application
- Open your browser and navigate to: `https://localhost:5001`
- The application will automatically seed the Driver and Passenger roles

### 🔧 Development Setup
For development with live reload:
```bash
dotnet watch run
```

### 📦 Database Management
```bash
# Create new migration
dotnet ef migrations add MigrationName

# Update database
dotnet ef database update

# Remove last migration (if not applied)
dotnet ef migrations remove
```

---

## 👥 Team Members and Individual Contributions

### 🔐 Team Member 1 (CE148_Sonani Het) - Authentication & Profile Management
**Responsibilities: User Authentication & Profile Management**

**Key Contributions:**
- **ASP.NET Core Identity Implementation**: Set up complete authentication system
  - Configured Identity services in `Program.cs`
  - Implemented role-based user registration system
  - Created secure login/logout functionality with cookie authentication
  
- **User Model & Database Design**: Designed comprehensive user system
  - Extended `ApplicationUser` model with custom fields
  - Created database migrations for user profiles
  - Implemented Entity Framework relationships
  
- **Profile Management System**: Built complete profile workflow
  - Developed `ProfileController` with CRUD operations
  - Created `ProfileCompletedAttribute` custom filter
  - Implemented role-based profile validation (Driver vs Passenger requirements)
  - Built profile edit views with proper validation

- **Security Features**: Ensured application security
  - Implemented CSRF protection with `[ValidateAntiForgeryToken]`
  - Created secure session management
  - Set up role-based authorization filters

**Files Implemented:**
- `Models/ApplicationUser.cs` - Extended Identity user model
- `Controllers/ProfileController.cs` - Profile management
- `Filters/ProfileCompletedAttribute.cs` - Custom validation filter
- `Areas/Identity/Pages/Account/` - Login/Register pages
- `Views/Profile/Edit.cshtml` - Profile editing interface
- Database migrations for user system

---

### 🚗 Team Member 2 (CE117_Moradiya Tilak) - Driver Functionality
**Responsibilities: Complete Driver Experience & Ride Management**

**Key Contributions:**
- **Ride Management System**: Built comprehensive ride creation and management
  - Developed `RideController` with full CRUD operations
  - Implemented ride creation with validation and future date checking
  - Created ride editing and deletion functionality
  - Built "My Rides" dashboard for drivers
  
- **Custom Validation**: Enhanced data integrity
  - Created `FutureDateAttribute` for ride date validation
  - Implemented business logic for ride availability
  - Added real-time seat count management
  
- **Driver-Specific Features**: Tailored experience for drivers
  - Role-based authorization with `[Authorize(Roles = "Driver")]`
  - Driver booking management and passenger oversight
  - Vehicle information integration in profiles
  - UPI payment information handling

- **Data Models**: Designed ride-related data structures
  - Created `Ride` model with comprehensive validation
  - Implemented proper relationships between rides and users
  - Set up database constraints and foreign keys

**Files Implemented:**
- `Controllers/RideController.cs` - Complete ride management
- `Models/Ride.cs` - Ride entity model
- `Models/FutureDateAttribute.cs` - Custom validation
- `Views/Ride/Create.cshtml` - Ride creation interface
- `Views/Ride/Edit.cshtml` - Ride editing interface
- `Views/Ride/Delete.cshtml` - Ride deletion confirmation
- `Views/Ride/MyRides.cshtml` - Driver dashboard
- `Views/Booking/DriverBookings.cshtml` - Driver booking management

---

### 🔍 Team Member 3 (CE041_Pansheriya Yagnik ) - Passenger Functionality
**Responsibilities: Complete Passenger Experience & Booking System**

**Key Contributions:**
- **Ride Discovery System**: Built comprehensive search and filtering
  - Implemented advanced ride search with location and date filters
  - Created `Search` action with EF.Functions.Like for flexible location matching
  - Developed ride details view with complete information display
  - Built responsive search interface with real-time filtering
  
- **Booking Management System**: Complete booking workflow
  - Developed `BookingController` with full booking lifecycle
  - Implemented instant booking confirmation system
  - Created booking cancellation functionality
  - Built "My Bookings" dashboard for passengers
  
- **User Interface & Experience**: Designed passenger-centric views
  - Created intuitive search interface with Bootstrap 5
  - Developed detailed ride information displays
  - Implemented responsive booking forms with seat selection
  - Built booking history and status tracking interfaces

- **Data Integration**: Passenger-focused data handling
  - Created `Booking` model with proper validation
  - Implemented seat availability real-time updates
  - Set up booking status management (Confirmed/Cancelled)
  - Integrated passenger information in ride displays

**Files Implemented:**
- `Controllers/BookingController.cs` - Complete booking system
- `Models/Booking.cs` - Booking entity model
- `Views/Ride/Search.cshtml` - Ride search interface
- `Views/Ride/Details.cshtml` - Detailed ride information
- `Views/Booking/Create.cshtml` - Booking creation interface
- `Views/Booking/MyBookings.cshtml` - Passenger dashboard
- `Views/Home/Index.cshtml` - Landing page with ride discovery
- Search and filtering logic in `RideController`

---

### 🤝 Collaborative Efforts
**Shared Responsibilities:**
- **Project Architecture**: All team members contributed to MVC structure design
- **Database Design**: Collaborative effort on Entity Framework relationships
- **UI/UX Consistency**: Coordinated Bootstrap 5 styling across all views
- **Testing & Debugging**: Cross-functional testing of integrated features
- **Code Reviews**: Peer review process for quality assurance
- **Documentation**: Collaborative documentation and README creation

---

## 🏗️ Project Structure
```
RideFusion/
├── Controllers/           # MVC Controllers
├── Models/               # Data Models
├── Views/                # Razor Views
├── Data/                 # Database Context
├── Areas/Identity/       # Authentication Pages
├── Filters/              # Custom Attributes
├── Migrations/           # Database Migrations
├── wwwroot/             # Static Files
└── README.md            # Project Documentation
```

---

## 🌟 Key Achievements
- **Complete Role-Based System**: Separate workflows for drivers and passengers
- **Real-Time Operations**: Dynamic seat management and instant bookings
- **Security Implementation**: Comprehensive protection against common vulnerabilities
- **User-Centric Design**: Intuitive interface with excellent user experience
- **Scalable Architecture**: Clean separation of concerns and maintainable code

---

## 🔮 Future Enhancements
- **Rating System**: Driver and passenger reviews
- **Real-time Chat**: In-app messaging between users
- **Payment Integration**: Online payment processing
- **Mobile App**: Native iOS/Android applications
- **GPS Integration**: Real-time location tracking
- **Push Notifications**: Booking updates and reminders

---
## 👥 Team

- **Het Sonani (CE148)** – Authentication, Security & User Management
- **Tilak Moradiya (CE117)** – Donation Management & Backend Logic
- **Yagnik Pansheriya (CE041)** – Frontend Development & NGO Matching
  
**Built with ❤️ using ASP.NET Core 8 and modern web technologies**
