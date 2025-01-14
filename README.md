# Dockerfile Bug: Missing requirements.txt

This repository demonstrates a common error in Dockerfiles: attempting to use a requirements.txt file before it has been added to the image's context.

## Bug Description:

The provided `Dockerfile` attempts to install Python dependencies using `pip3 install -r requirements.txt`.  However, the `COPY requirements.txt .` command is placed *before* the `requirements.txt` file is actually present in the build context. This results in a build failure because the file is not found.

## Solution:

The corrected `Dockerfile-fixed` file reorders the `COPY` commands, ensuring that `requirements.txt` is copied *before* the `RUN pip3 install` command.
