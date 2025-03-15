# Paired Photo Retrieval Workflow

This repository documents the workflow for dynamic retrieval and presentation of paired photographic assets from a Digital Asset Management (DAM) system. It focuses on the interaction between a client-side interface and a DAM system to retrieve and display related images, such as front and back views of a photograph.

![archive_photo_stitcher](https://github.com/user-attachments/assets/166fa493-f01d-4f9d-80b8-6d51edd68896)


The ideal workflow begins when a client-side interface requests a specific photographic asset from a Digital Asset Management (DAM) system. It does so by sending a metadata retrieval request to the DAM API, including a unique identifier for the desired photograph.

Upon receiving the request, the DAM API queries the DAM database to retrieve the associated metadata. The database responds with the metadata, which the API then forwards to the client-side interface.

The interface analyses the metadata to determine key attributes, such as whether the image is a front or back view. This step is essential for retrieving the corresponding photograph.

Next, the client-side interface sends another metadata request to the DAM API, this time for the related photograph. The request includes an identifier linking the current image to its counterpart (e.g., the back view if the initial request was for the front view).

The DAM API queries the database again and returns the metadata for the related photograph, which is then passed back to the client-side interface.

With both sets of metadata retrieved, the interface constructs a playlist, ensuring the photographs are presented in a logical order (e.g., front view before back view).

The interface then communicates with the DAM API to create and store a playlist object in the DAM system. The API interacts with the database to save the playlist and returns a playlist identifier.

Finally, the client-side interface uses this identifier to embed a media player in the user interface. The player loads the dynamically generated playlist, displaying the paired photographic assets to the user.

Throughout the process, error-handling mechanisms ensure that if a requested photograph or its counterpart is missing, appropriate messages inform the user.

As a means to illustrate the ideation above, a simple web application to retrieve and embed Kaltura media entries and their associated flip side entries side by side using the Kaltura API is included, thus:

![image](https://github.com/user-attachments/assets/dfc6105c-7a67-4a54-b956-4421f77f2102)

