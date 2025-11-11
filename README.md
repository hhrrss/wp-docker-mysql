# WordPress Docker Development Environment

A lightweight Docker-based setup for local WordPress development with a MySQL database and bind-mounted code for live editing.

---

## 🚀 Quick Start

1. **Clone the repository**

   ```bash
   git clone https://github.com/hhrrss/wp-docker-mysql.git
   cd wp-docker-mysql
   ```

2. **Create the local WordPress directory**

   ```bash
   mkdir wordpress
   ```

3. **Start the containers**

   ```bash
   docker-compose up -d
   ```

4. **Access WordPress**

   Open [http://localhost:8080](http://localhost:8080) in your browser and complete the installation wizard.

---

## 🧩 Project Structure

```
.
├── docker-compose.yml     # Docker setup for WordPress + MySQL
├── wordpress/              # Local bind-mounted WordPress codebase
├── .gitignore
└── README.md
```

---

## 🛠️ Development Workflow

- Edit any WordPress file locally (themes, plugins, etc.) in `./wordpress/`.
- Changes are reflected instantly in the container.
- Database data persists via the named volume `db_data`.

### Common Commands

| Action | Command |
|--------|----------|
| Start containers | `docker-compose up -d` |
| Stop containers | `docker-compose down` |
| View logs | `docker-compose logs -f` |
| Rebuild environment | `docker-compose up --build -d` |

---

## 🧰 Optional: phpMyAdmin

If you want to manage the database through a web UI, you can add this service to your `docker-compose.yml`:

```yaml
phpmyadmin:
  image: phpmyadmin:latest
  depends_on:
    - db
  ports:
    - "8081:80"
  environment:
    PMA_HOST: db
    MYSQL_ROOT_PASSWORD: root
```

Then visit [http://localhost:8081](http://localhost:8081).

---

## 🧹 Cleanup

To remove everything (including DB data):

```bash
docker-compose down -v
```

---

## 📄 License

MIT — do whatever you like with it.
