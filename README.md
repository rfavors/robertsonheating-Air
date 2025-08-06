# Robertson & Agnew Heating and Air Website

A professional static website for Robertson & Agnew Heating and Air services.

## Coolify Deployment Instructions

### Prerequisites
- Coolify instance running on IP: 154.38.171.185
- Domain name configured to point to your Coolify server

### Deployment Steps

1. **Create New Project in Coolify**
   - Log into your Coolify dashboard at `http://154.38.171.185:8000`
   - Create a new project
   - Choose "Docker Compose" as the deployment type

2. **Repository Setup**
   - Connect your Git repository containing this code
   - Coolify will automatically detect the `docker-compose.yml` file

3. **Configure Basic Authentication**
   To enable password protection with username "boss" and password "robertson":
   
   - Generate password hash:
   ```bash
   htpasswd -nb boss robertson
   ```
   
   - Update the docker-compose.yml labels section:
   ```yaml
   labels:
     - "traefik.http.middlewares.robertson-auth.basicauth.users=boss:$$2y$$12$$[generated-hash]"
     - "traefik.http.routers.robertson-website.middlewares=robertson-auth"
   ```

4. **Domain Configuration**
   - Update the Host rule in docker-compose.yml:
   ```yaml
   - "traefik.http.routers.robertson-website.rule=Host(`yourdomain.com`)"
   ```

5. **Deploy**
   - Click "Deploy" in Coolify
   - The website will be available at your configured domain with HTTPS

### Features
- Responsive design
- Professional service pages
- Contact forms
- Service area information
- Testimonials
- Maintenance plans

### File Structure
- `index.html` - Homepage
- `about-us.html` - About page
- `residential.html` - Residential services
- `commercial.html` - Commercial services
- `yearly-maintenance.html` - Maintenance plans
- `contact-us.html` - Contact information
- `styles.css` - Main stylesheet
- `script.js` - JavaScript functionality
- `images/` - Image assets

### Authentication
When basic auth is enabled, users will be prompted for:
- Username: `boss`
- Password: `robertson`

### Support
For deployment issues, check the Coolify logs or contact your system administrator.