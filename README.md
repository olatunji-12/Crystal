**🐾 HOSTING A STATIC WEB APPLICATION ON AZURE VIRTUAL MACHINE WITH CUSTOM DOMAIN CONFIGURATION USING AMAZON ROUTE 53**

**📦 PART 1: Set Up VM, Copy Web App Files, and Install Required Software**

Create a Virtual Machine and log into it via SSH or password authentication.

Install Git (if you're cloning from a GitHub repo and using Git terminal): sudo apt install -y git

If you're not using Git, upload files using scp, FTP, or any other method.

Clone Your GitHub Repository: git clone https://github.com/olatunji-12/Crystal.git

Navigate into the project directory: cd Crystal

Install Nginx: sudo apt update && sudo apt install -y nginx

Check Nginx status: sudo systemctl status nginx

Copy your project files to Nginx’s web root: sudo cp -r Crystal/* /var/www/html/

Configure Nginx for your custom domain: sudo nano /etc/nginx/sites-available/default

For Domain name "animalsforalllives.com";

Replace the contents with:

server {
    listen 80;
    server_name animalsforalllives.com www.animalsforalllives.com;

    root /var/www/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

Save and exit (CTRL + O, ENTER, then CTRL + X).

Restart Nginx: sudo systemctl restart nginx

**🌐 PART 2: Configure DNS for Your Azure VM**

**This project uses Amazon Route 53 for DNS management.**

Go to the Amazon Route 53 dashboard

Under DNS Management, click on Hosted Zones

Select your domain and click Create Record.

Create an A Record and populate the fields as follows:

Record name: @ or leave blank

Record type: A – IPv4 address

Value: Your Azure VM's public IP (e.g., 172.200.170.16)

TTL: 300 (default)

Create the record by confirming the configuration.

(Optional) Create a CNAME Record:

Record name: www

Record type: CNAME

Value: animalsforalllives.com

TTL: 300

Wait for DNS propagation (can take up to 48 hours).

Check status via: nslookup animalsforalllives.com

Or use https://dnschecker.org:

Enter domain name

Select record type (A or CNAME)

Click search

✅ A green tick confirms DNS propagation.

**💻 Final Testing**
Once DNS is active:

Visit your site via:

http://animalsforalllives.com

Or test using your VM's IP address:

http://172.200.170.16

**🚀 Technologies Used**
Microsoft Azure – for Virtual Machine provisioning

Amazon Route 53 – for DNS hosting and domain management

Linux (Ubuntu Server) – operating system on VM

Nginx – static web server and reverse proxy

HTML & CSS – for website content and styling

Git & GitHub – for version control and source code management

SSH – for remote access to VM

DNS Tools – like nslookup and dnschecker.org for testing propagation



🌐 **Live URL**: https://olatunji-12.github.io/Crystal/

📂

🚀 **Hosted on**: GitHub Pages  
☁️ **Originally hosted on**: Azure Virtual Machine with custom domain `animalsforalllives.com`

---

## 🔧 How to Use Locally

1. Clone the repository: git clone https://github.com/olatunji-12/Crystal.git
