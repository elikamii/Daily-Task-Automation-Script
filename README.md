import os
import shutil
import datetime

def organize_files(source_dir, destination_dir):
    """Organizes files by creating date-stamped folders and moving them."""
    if not os.path.exists(destination_dir):
        os.makedirs(destination_dir)

    today = datetime.date.today()
    folder_name = today.strftime("%Y-%m-%d")
    destination_path = os.path.join(destination_dir, folder_name)

    if not os.path.exists(destination_path):
        os.makedirs(destination_path)
    
    for filename in os.listdir(source_dir):
        source_path = os.path.join(source_dir, filename)
        if os.path.isfile(source_path):
            try:
                shutil.move(source_path, destination_path)
                print(f"Moved: {filename}")
            except Exception as e:
                print(f"Could not move {filename}: {e}")

    print(f"All files from {source_dir} have been processed.")
    
# Example usage
# organize_files("C:/Users/YourName/Desktop/MyDownloads", "C:/Users/YourName/Desktop/OrganizedFiles")
