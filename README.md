# Benchmark de Ejecución en PySpark con GCP Dataproc

Este repositorio contiene los scripts y el procedimiento paso a paso para ejecutar y evaluar el rendimiento del pipeline de datos de trabajos de LinkedIn utilizando **PySpark** sobre un clúster distribuido en **Google Cloud Platform (GCP) Dataproc**.

---

## 📋 Prerrequisitos

1. **Cuenta en Google Cloud Platform (GCP)** con créditos activos.
2. **Google Cloud SDK (`gcloud`)** instalado y configurado localmente o mediante GCP Cloud Shell.
3. Archivos de datos (`postings`, `skills`, `job_summary`) subidos a un bucket de **Google Cloud Storage (GCS)** en formato CSV o Parquet.

---

## 🚀 Paso 1: Creación del Clúster de Dataproc

Creamos un clúster de Dataproc optimizado con 1 nodo Máster y 2 nodos Workers (`n1-standard-2` con 8 GB de RAM cada uno):

```bash
gcloud dataproc clusters create cluster-proyecto \
    --region=us-west1 \
    --zone=us-west1-c \
    --master-machine-type=n1-standard-2 \
    --master-boot-disk-size=50GB \
    --num-workers=2 \
    --worker-machine-type=n1-standard-2 \
    --worker-boot-disk-size=50GB \
    --image-version=2.1-debian11
