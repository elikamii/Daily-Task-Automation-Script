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
        if os.path.isfile(os.path.join(source_dir, filename)):
            shutil.move(os.path.join(source_dir, filename), destination_path)
    print(f"Files from {source_dir} moved to {destination_path}")

# Example usage
# organize_files("C:/Users/YourName/Desktop/MyDownloads", "C:/Users/YourName/Desktop/OrganizedFiles")
