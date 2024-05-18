    FROM python:3.12.0-slim-bookworm

    ENV PYTHONBUFFERED 1
    ENV PYTHONWRITEBYTECODE 1

    ENV APP=/app

    # Change the workdir.
    WORKDIR /server

    # Install the requirements
    COPY requirements.txt requirements.txt

    RUN pip3 install -r requirements.txt

    # Copy the rest of the files
    COPY . ./

    EXPOSE 8000

    RUN chmod +x /server/entrypoint.sh

    ENTRYPOINT ["/bin/bash","/server/entrypoint.sh"]

    CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]