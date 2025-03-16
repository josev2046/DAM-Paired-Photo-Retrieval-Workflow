# Paired Photo Retrieval Workflow

This repository documents the workflow for dynamic retrieval and presentation of paired photographic assets from a Digital Asset Management (DAM) system. It focuses on the interaction between a client-side interface and a DAM system to retrieve and display related images, such as front and back views of a photograph.

![archive_photo_stitcher](https://github.com/user-attachments/assets/166fa493-f01d-4f9d-80b8-6d51edd68896)


This pattern begins with a client-side interface that requests a specific photographic asset from a Digital Asset Management (DAM) system. It does so by sending a metadata retrieval request to the DAM API, including a unique identifier for the desired photograph.

Upon receiving the request, the DAM API queries the DAM database to retrieve the associated metadata. The database responds with the metadata, which the API then forwards to the client-side interface.

The interface analyses the metadata to determine key attributes, such as whether the image is a front or back view. This step is essential for retrieving the corresponding photograph.

Next, the client-side interface sends another metadata request to the DAM API, this time for the related photograph. The request includes an identifier linking the current image to its counterpart (e.g., the back view if the initial request was for the front view).

The DAM API queries the database again and returns the metadata for the related photograph, which is then passed back to the client-side interface.

With both sets of metadata retrieved, the interface constructs a playlist, ensuring the photographs are presented in a logical order (e.g., front view before back view).

The interface then communicates with the DAM API to create and store a playlist object in the DAM system. The API interacts with the database to save the playlist and returns a playlist identifier.

Finally, the client-side interface uses this identifier to embed a media player in the user interface. The player loads the dynamically generated playlist, displaying the paired photographic assets to the user.

Throughout the process, error-handling mechanisms ensure that if a requested photograph or its counterpart is missing, appropriate messages inform the user.

Now, while the academic, vendor-agnostic approach outlined above is broadly applicable, here’s a practical interpretation of how it might work in the real world. In this app I use the Kaltura API (it's what I had at hand) to fetch media entries and their corresponding flip-side entries, displaying them side by side:

![image](https://github.com/user-attachments/assets/1a82092a-ad1b-4082-9686-32d3d9e8ee2d)

## Walk-through

https://github.com/user-attachments/assets/e8960f0f-9a79-4e98-a2c9-87c5516b3f6d

## Features
- Input a Kaltura Entry ID to fetch its metadata.
- Extracts the flip side Entry ID from a predefined custom metadata field.
- Embeds both the searched entry and its flip side entry as Kaltura players in iframes, displayed side by side.
- Error handling for API requests and XML parsing.

## Prerequisites
- A Kaltura account with:
  - Partner ID
  - User Secret (Admin or User secret, depending on access needs)
  - Custom Metadata Schema
- Modern browser with support for `fetch`, `DOMParser`, and `URLSearchParams`.

  

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.15033283.svg)](https://doi.org/10.5281/zenodo.15033283)


