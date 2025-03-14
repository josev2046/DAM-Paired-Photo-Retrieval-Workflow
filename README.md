# Paired Photo Retrieval Workflow

This repository documents the workflow for dynamic retrieval and presentation of paired photographic assets from a Digital Asset Management (DAM) system. It focuses on the interaction between a client-side interface and a DAM system to retrieve and display related images, such as front and back views of a photograph.

![archive_photo_stitcher](https://github.com/user-attachments/assets/166fa493-f01d-4f9d-80b8-6d51edd68896)


The workflow begins when a client-side interface requires the retrieval of a specific photographic asset from a Digital Asset Management (DAM) system. This request is initiated by the client-side interface, which sends a metadata retrieval request to the DAM API, including a unique identifier for the desired photograph.

Upon receiving the request, the DAM API proceeds to query the DAM database to locate and retrieve the metadata associated with the provided identifier. The DAM database responds by returning the requested metadata to the DAM API, which in turn forwards this information to the client-side interface.

The client-side interface then analyzes the retrieved metadata to determine specific attributes of the photograph, such as whether it represents the front or back view. This determination is crucial for the subsequent retrieval of the related photographic asset.

Following this, the client-side interface issues another metadata retrieval request to the DAM API, this time targeting the related photograph. This request includes an identifier that links the current photograph to its counterpart (e.g., the back view if the current photo is the front view).

The DAM API again queries the DAM database to retrieve the metadata for the related photograph. The DAM database returns the relevant metadata to the DAM API, which then transmits it back to the client-side interface.

With the metadata for both photographs now available, the client-side interface proceeds to construct a playlist. This playlist is designed to present the paired photographic assets in a logical sequence, such as displaying the front view before the back view.

The client-side interface then interacts with the DAM API to create and persist a playlist object within the DAM system. This involves sending a request to the DAM API, which in turn interacts with the DAM database to store the playlist. The DAM API responds by providing a playlist identifier.

Finally, the client-side interface utilizes the obtained playlist identifier to embed a media player within the user interface. This media player is configured to load and display the dynamically generated playlist, thereby presenting the paired photographic assets to the user.

Throughout this process, the client-side interface incorporates error handling mechanisms to manage scenarios where a requested photograph or its related counterpart cannot be found within the DAM system. In such cases, appropriate error messages are displayed to inform the user of the issue.
