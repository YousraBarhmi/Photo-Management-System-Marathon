# Smart Photo Management System for Sports Events

This project revolutionizes the management and interaction with photos taken at sports events. By leveraging cutting-edge machine learning and text mining, this intelligent application provides an efficient solution for organizing, managing, and accessing event photos.

## Features

* **Bulk Photo Upload**: Facilitates quick and secure uploading of large volumes of photos.
* **Automatic Photo Classification**: Uses image recognition to detect and categorize bib numbers in photos, organizing them automatically.
* **Bib Number Search**: Enables participants to easily locate their photos by entering their bib number.
* **Intuitive Interface**: Designed to be user-friendly for both professional photographers and event participants.

## Example of Use

### Uploading Photos

1. **Navigate to the Upload Page**:
   - Go to the upload page where you can start adding your photos.
   - ![Upload Interface](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/299ecf21-afca-401e-bc50-f232d17b02c2)

2. **Select Photos to Upload**:
   - Click on the upload button to open the file selection dialog.
   - Choose the photos you want to upload from your local system.
   - ![File Selection](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/e5b91f8b-e312-4cef-b133-da455f3b3c8e)

### Searching for Photos

1. **Navigate to the Search Page**:
   - Go to the search page to find specific photos from the database.
   - ![Search Interface](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/86deee1f-4237-44d4-91b9-7a49dbe676da)

2. **Enter Search Criteria**:
   - Enter keywords or other criteria in the search bar to find the photos you need.
   - ![Search Results](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/55ebdf06-a8d5-4806-86e7-72d068b6e2b0)

3. **View Search Results**:
   - The results matching your search criteria will be displayed as thumbnails.
   - ![Detailed View](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/9907309c-b4a2-460c-9a9d-41f32b441473)
   - ![image](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/c3c4ee5a-8513-4631-862d-4564dac7c707)

4. **Handling No Results**:
   - If no photos match your search criteria, a "No image found" message will be displayed.
   - ![No Image Found](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/ee6f0a0a-85f2-4811-919c-67411fa3e693)


### Prerequisites

* Python 3.7 or higher
* PyTorch
* YOLOv8 model files
* Additional Python libraries listed in `requirements.txt`

### Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/YousraBarhmi/Photo-Management-System-Marathon.git
    cd sports-event-photo-management
    ```

2. **Create a virtual environment**:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install required libraries**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Download the YOLOv8 model weights**:
    ```bash
    mkdir -p models/yolov8
    # Download and place the yolov8s.pt file in the models/yolov8 directory
    ```

## Usage

1. **Prepare your dataset**: Ensure it follows the structure defined in `data.yaml`.

2. **Train the YOLOv8 model**:
    ```python
    !yolo task=detect mode=train model=models/yolov8/yolov8s.pt data=data/data.yaml epochs=25 imgsz=800 plots=True
    ```

3. **Evaluate the model's performance**:
    - Review the training results in the generated plots.
    - Analyze the confusion matrix and performance metrics.

4. **Classify and manage event photos**:
    ```python
    from your_module import PhotoManager
    manager = PhotoManager(model_path="models/yolov8/yolov8s.pt", data_path="data/data.yaml")
    manager.classify_and_upload_photos("path_to_photos")
    ```

## Results Interpretation

* **Loss Graphs**: Display the reduction in box, classification, and DFL loss over epochs, indicating improved performance.
* **Performance Metrics**: Precision, recall, and mAP metrics provide insight into the model's accuracy and effectiveness.

### Confusion Matrix Example

```
    332   55
     14    0
```

![image](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/3f461a59-9d68-4f4e-ab7b-7d5712a3002c)

* **Recall Curve**: Shows the model's capability to detect objects.
* **Precision Curve**: Reflects the accuracy of the detected objects.
* **F1 Score Curve**: Balances precision and recall.

![image](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/1a32fff9-f933-499c-8238-974e10300fc9)  ![image](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/9ad9c0cc-c038-4869-a869-19480186072e)  ![image](https://github.com/YousraBarhmi/Photo-Management-System-Marathon/assets/138295122/04a02812-6278-4e31-99d0-0a791c023b2f)
   
## Future Work

* **Hyperparameter Tuning**: Enhance model performance through further tuning.
* **Cross-Validation**: Implement to ensure robust generalization.
* **Error Analysis**: Identify and improve performance on challenging classes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
