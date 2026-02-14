# Project Dashboard

A modern, responsive project management dashboard built with Next.js, TypeScript, and Tailwind CSS.

## Features

- **Project Management**: Create, view, and manage projects with details like location, project manager, and PIC
- **Task Tracking**: Add tasks with status (Done, Progress, Problem) and due dates
- **Status Monitoring**: Real-time project status tracking (Total, Progress, Urgent, Done)
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Modern UI**: Built with shadcn/ui components and smooth animations with Framer Motion
- **Late Task Alerts**: Visual indicators for overdue tasks

## Tech Stack

- **Framework**: Next.js 16 with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui (Card, Button, Badge)
- **Animations**: Framer Motion
- **Icons**: Lucide React

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn

### Installation

1. Install dependencies:
```bash
npm install
```

2. Run the development server:
```bash
npm run dev
```

3. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Usage

### Adding a Project

1. Click the "+ Add Update" button
2. Fill in the project details:
   - Project Name
   - Location
   - Project Manager
   - Due Date
   - PIC (Person in Charge)
   - PIC Role
3. Click "Save Project"

### Managing Tasks

1. Click "Detail" on any project to view its details
2. Add tasks with:
   - Task description
   - Due date
   - Status (Done, Progress, Problem)
3. Update task status using the dropdown
4. Delete tasks with the trash icon

### Project Status

- **Progress**: Yellow badge - Active projects
- **Urgent**: Red badge - Projects with problems
- **Done**: Green badge - Completed projects
- **⚠️ Warning**: Indicates overdue tasks

## Deployment

### Build for Production

```bash
npm run build
```

### Start Production Server

```bash
npm start
```

### Deploy to Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to [Vercel](https://vercel.com)
3. Deploy automatically

### Deploy to Other Platforms

The application can be deployed to any platform that supports Next.js:
- Netlify
- Railway
- Digital Ocean
- AWS Amplify

## Project Structure

```
src/
├── app/
│   ├── page.tsx          # Main dashboard component
│   ├── layout.tsx        # Root layout
│   └── globals.css       # Global styles
├── components/
│   └── ui/               # shadcn/ui components
│       ├── button.tsx
│       ├── card.tsx
│       └── badge.tsx
└── lib/
    └── utils.ts          # Utility functions
```

## Customization

### Adding New Status Types

1. Update the status options in the select elements
2. Modify the `getProjectStatus` function
3. Update the `StatusBadge` and `TaskBadge` components

### Styling

The application uses Tailwind CSS with a custom theme. Modify `tailwind.config.js` to customize colors, spacing, and other design tokens.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

For questions or issues, please open an issue on the GitHub repository.
