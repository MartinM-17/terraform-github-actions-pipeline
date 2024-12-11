
```markdown
# Terraform GitHub Actions Pipeline

Este proyecto demuestra cómo automatizar la implementación de infraestructura en AWS utilizando Terraform, GitHub Actions y Terraform Cloud. El flujo de trabajo incluye la configuración de un pipeline CI/CD para desplegar recursos de AWS mediante un enfoque automatizado y colaborativo.



## Prerrequisitos
1. Una cuenta de GitHub.
2. Una cuenta de Terraform Cloud (HCP).
3. Una cuenta de AWS.

## Configuración

### AWS IAM y Credenciales
- Crear un grupo de IAM llamado `GitHub-Actions-Groups` con políticas:
  - `AmazonEC2FullAccess`
  - `S3ReadOnlyAccess`
- Crear un usuario `github-actions-user_1` y asociarlo al grupo.
- Generar claves de acceso y guardarlas como secretos en GitHub Actions.

### Terraform Cloud
- Crear un workspace llamado `Terraform-Pipeline-Workspace` con flujo `API-driven`.
- Configurar credenciales de AWS y token de API en el workspace.

### Secretos en GitHub Actions
- En el repositorio de GitHub, navegar a **Settings > Secrets and Variables > Actions**.
- Crear los siguientes secretos:
  - `TF_API_TOKEN`: Token de API de Terraform Cloud.
  - `AWS_ACCESS_KEY_ID` y `AWS_SECRET_ACCESS_KEY`: Credenciales de AWS.

## Pipeline de GitHub Actions
El pipeline se define en `.github/workflows/terraform-pipeline.yml` y ejecuta:
1. **Checkout del repositorio**.
2. **Inicialización de Terraform**.
3. **Ejecución de Terraform Plan y Apply**.

## Validación
1. Modificar un archivo (por ejemplo, `main.tf`).
2. Realizar commit y push:
   ```bash
   git add .
   git commit -m "Prueba de pipeline Terraform con GitHub Actions"
   git push origin main
3. Verificar la ejecución en la pestaña **Actions** de GitHub.
4. Validar los recursos creados en AWS y Terraform Cloud.
   ```

## Recursos
Este proyecto incluye:
- `main.tf`: Define recursos como EC2, VPC y Security Groups.
- `variables.tf`: Variables de configuración.
- `output.tf`: Salidas del despliegue.
- `.github/workflows/terraform-pipeline.yml`: Pipeline de GitHub Actions.

## Destruir Recursos
Para evitar costos innecesarios, destruir los recursos creados:
```bash
terraform destroy -auto-approve
```

## Enlaces
- [Repositorio GitHub](https://github.com/MartinM-17/terraform-github-actions-pipeline)
- [Terraform Cloud](https://app.terraform.io/)
- [AWS Console](https://aws.amazon.com/console/)

---

### Estructura del proyecto

```plaintext
terraform-github-actions-pipeline/
├── .github/
│   └── workflows/
│       └── terraform-pipeline.yml
├── main.tf
├── variables.tf
├── output.tf
├── README.md
```

---
