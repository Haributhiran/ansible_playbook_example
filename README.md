# 📦 GraphQL Binary Installer via Ansible

This Ansible playbook automates the process of:

1. Connecting to a GraphQL endpoint (`apple.com`)
2. Sending an authenticated GraphQL POST request
3. Downloading a ZIP package from the response
4. Extracting the package
5. Running an installation script (`install.sh`) from the extracted directory

---

## 🧾 Prerequisites

- Ansible installed on the control machine
- Target machine has:
  - `curl`, `unzip`, `bash` installed
  - SSH access configured
- GraphQL endpoint provides a downloadable ZIP binary via POST request

---

## 🔧 Configuration

Update the following variables in the playbook:

| Variable        | Description                                    |
|----------------|------------------------------------------------|
| `gql_url`       | The GraphQL API endpoint                      |
| `auth_token`    | Bearer token for authentication               |
| `query`         | GraphQL query to get the download link        |
| `temp_path`     | Directory where the ZIP file will be stored   |
| `zip_filename`  | Name to save the downloaded ZIP file as       |
| `install_script`| Name of the `.sh` file to execute             |

> **Note**: If the query response is a URL to the ZIP file, adjust the playbook to use `get_url` instead of saving raw content.

---

## ▶️ How to Run

```bash
ansible-playbook -i inventory install_binary.yml
