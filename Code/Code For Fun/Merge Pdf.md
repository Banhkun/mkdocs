```python
from PyPDF2 import PdfMerger
import os

# Path to the folder containing chapter PDFs (update if needed)
pdf_folder_path = "/content/drive/MyDrive/path_to_your_chapters"  # Change this to your actual folder

# Output folder for volumes
output_folder_path = os.path.join(pdf_folder_path, "Volumes")
os.makedirs(output_folder_path, exist_ok=True)

# Helper function to generate filenames
def get_pdf_filename(chapter_number):
    return f"Chapter {chapter_number}.pdf"

# Define the volume ranges
volume_ranges = [
    (1, 9),
    (10, 19),
    (20, 29),
    (30, 39),
    (40, 50),
    (51, 60),
    (61, 70),
    (71, 80),
    (81, 90),
    (91, 100),
    (101, 110),
    (111, 120),
    (121, 130),
    (131, 140),
    (141, 150),
    (151, 160),
    (161, 170),
    (171, 180),
    (181, 190),
    (191, 200)
]

# Merge PDFs into volumes
for idx, (start_chapter, end_chapter) in enumerate(volume_ranges, start=1):
    merger = PdfMerger()
    for chapter_num in range(start_chapter, end_chapter + 1):
        filename = get_pdf_filename(chapter_num)
        filepath = os.path.join(pdf_folder_path, filename)
        if os.path.exists(filepath):
            merger.append(filepath)
        else:
            print(f"⚠️ Missing: {filepath}")
    volume_filename = f"Volume {idx}.pdf"
    volume_path = os.path.join(output_folder_path, volume_filename)
    merger.write(volume_path)
    merger.close()
    print(f"✅ Created {volume_filename}")

print("🎉 All volumes created successfully!")

```

