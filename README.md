# img2pdf
This program is called img2pdf, but really I should have called it bag_of_bags_of_imgs_to_bag_of_pdfs, or something ridiculous like that. Basically, img2pdf bulk converts a set of directories containing image files to a set of PDF files. Here's how it works:

Let's say you have a collection of comics in the form of image scans. for some people, it's no fun to flip through folders of hundreds of images when you just want to read a book. Wouldn't it be nice if we could just bulk convert each folder to a PDF containing all of the images? Well, that's exactly what img2pdf does! I created this program to batch convert sets of comics in RAW format (named folders containing ordered images of pages). Here's an example of how it works:

1. Run the program (img2pdf.exe in the img2pdf folder) and it asks you to enter the path of a directory. This is the root director that contains other folders of scanned comics. Let's say you just call the root directory "Comics". To get the path, navigate to this directory in windows, open it, and you should be able to copy the path from the path bar just next to the search bar. Paste this path in the program and hit enter.

3. The program then asks you to enter a compression value. If you wish to reduce the resolution of your images a little to save space, you can enter some value between 0 and 100. 85 is strongly recommended if you want compression. If you want to preserve the resolution as much as possible, just type 100 and hit enter.

4. The program will then create a new folder in the Comics directory called 'pdf_files', loop through every folder in the Comics directory, create a PDF from the stored images in each directory, and save each pdf in the pdf_files folder. Each PDF file will be named after the parent folder for each set of images. That's it! It's super easy.

Some notes:
The program does a few operations to optimize the output PDF. 

1. Firstly, most images will be natively color images, even if they don't look like it. img2pdf does a calculation to see if each image could appropriately be converted to greyscale format, and will do the conversion if so. This saves a bit of space. 

2. For each image, if the height is larger than 2000 pixels, the image will be rescaled so that it's 2000 pixels tall. This ends up saving lots of space in cases where RAW images are unnecessarily large.

3. The program will occasionally do some renaming of folders. If your folder names have square brackets in them, Windows tends to throw a fit, so img2pdf will convert the name to only use standard brackets.

Troubleshooting:

YOUR FOLDER STRUCTURE MUST BE CORRECT. Your parent folder should contain only child folders (one for each comic), and each child folder should contain only images. There are controls to deal with non-image objects in the child folders, but it may be a source of error. Try to avoid having any zipped folders or nested child folders (a child folder within a child folder) as this will prevent the convert from working with that comic.

img2pdf has been through lots of rounds of iteration and improvements. To date, I have used it to process hundreds of folders and hundreds of thousands of images. It's at a point now where it almost never fails, but odd characters in folder names or very strange image files may cause the program to crash. If you encounter this, try renaming your folders with standard ASCII characters, or converting your image files to a standard format like PNG or JPEG.

IF img2pdf CRASHES -> The program will terminate right away if you have run it by double clicking the img2pdf.exe file. If you would like to examine the error message that caused the program to crash, try running img2pdf.exe from the Windows command like instead. 

For those of you who don't run command line programs often, if you click in the terminal while the program is running, it may pause the program. If the program seems frozen, try hitting enter in the terminal and waiting a bit, and progress should resume.

img2pdf was written in Python and packaged with PyInstaller, if that matters to anyone.
