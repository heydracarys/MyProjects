# MyProjects 
#1 Hey,this is my first project and i am so happy and proud creating it.hope you will like it.
# Program to Sort files into the matching folders.This is a very useful program to sort files and make the directory look clean

import os
def createFolder(folder): # Function to create folder if it doesn't already exists.
    if not os.path.exists(folder):
        os.makedirs(folder)

def sortFiles(foldername,filenames): # Function to sort files into the folders.
    for filename in filenames:
        os.replace(filename,f"{foldername}/{filename}")

files=os.listdir() 
files.remove("TrashCleaner.py")
createFolder('Images')
createFolder('Documents')
createFolder('Media')
createFolder('Others')

imgExt=[".png", ".jpg", ".jpeg", ".tif"]  #list of extensions of image files
images=[file for file in files if os.path.splitext(file)[1].lower() in imgExt ]
print(images)

docsExt=[".doc", ".docx", ".txt", ".pdf"]  #list of extensions of Documents
docs=[file for file in files if os.path.splitext(file)[1].lower() in docsExt]
print(docs)

mediaExt=[".mp3", ".mp4", ".m4a", "flv"]  #list of extensions of Media files
medias=[file for file in files if os.path.splitext(file)[1].lower() in mediaExt]
print(medias)

others=[] #list of extensions of other files
for file in files:
    allExt=os.path.splitext(file)[1].lower() 
    if (allExt not in imgExt) and (allExt not in mediaExt) and (allExt not in docsExt) and os.path.isfile(file):
        others.append(file)
print(others)

sortFiles("Images",images)
sortFiles("Documents",docs)
sortFiles("Media",medias)
sortFiles("Others",others)
    
        

