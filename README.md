# PythonPdf
#Apuntes PDF en python. 
###############################WORKING PDF Y WORD DOCUMENTS
###Como son binarios tu necesitas hacer algo m as que un un simple open()


#PyPDF2 and Python-Docx

#read pdf and crafting new pdfs

##import PyPDF2
##
##
##pdfFileObj=open("meetingminutes.pdf","rb")
##pdfReader=PyPDF2.PdfFileReader(pdfFileObj)
##print(pdfReader.numPages)    #Numero de paginas.
##pageObj=pdfReader.getPage(3)   #Coges la pagina
##print(pageObj.extractText()) # Extraes el texto
##
##pdfFileObj.close()   #Se cierra


#######################
##import PyPDF2
##
###pdfReader=PyPDF2.PdfFileReader(open("encrypted.pdf","rb"))
###pdfReader.isEncrypted  #True o False
###pdfReader.getPage(0)   #Lanza error porque esta encriptado
##pdfReader=PyPDF2.PdfFileReader(open("encrypted.pdf","rb"))
##pdfReader.decrypt("rosebud")
##pdfReader.getPage(0)
##pageObj=pdfReader.getPage(0)
##print(pageObj.extractText())
##pdfFileObj.close()


################CREATING PDFS
#PyPDF2 no puede escribir en pdfs como python lo hace en archivos de texto.

##########PdfFileReader #
##########PdfFileWriter #
#copiar paginas de otros pdfs.rar paginas,overlayin paginas y encriptarlas
#para hacerlo como mucho tienes que crear nuevo pdf y pegar contenido en el
#1###Abre un pdf o mas pdfs existentes
#2###
#3#Copia pages from the PdfFileReader dentro de PdfFileWriter objet
#4Finally, use the PdfFileWriter to wirhte the output PDF

 ###############################Copying Pages
##
##import PyPDF2
##
##pdf1File=open("meetingminutes.pdf","rb")    ##Abre un archvio en lectua de binarios
##pdf2File=open("meetingminutes2.pdf","rb")  ##Lee un archivo en lectura de binarios
##
##
##pdf1Reader=PyPDF2.PdfFileReader(pdf1File)   ###Pasa al lector el objeto
##pdf2Reader=PyPDF2.PdfFileReader(pdf2File)     ###Pasa al lector el objeto
##
##
##
##pdfWriter=PyPDF2.PdfFileWriter()            #
##
##for pageNum in range(pdf1Reader.numPages):   ##devuelve un enero
##    pageObj=pdf1Reader.getPage(pageNum)
##    pdfWriter.addPage(pageObj)
##
##for pageNum in range(pdf2Reader.numPages):   ##devuelve un enero
##    pageObj1=pdf2Reader.getPage(pageNum)
##    pdfWriter.addPage(pageObj1)
##
##
##
##pdfOutputFile=open("combinedminutes.pdf","wb")
##pdfWriter.write(pdfOutputFile)
##pdfOutputFile.close()
##pdf1File.close()
##pdf2File.close()
###PyPDf2 no puede añadir hojan en el medio siempre sera en la ultima pagina
################################################################################

#################ROTAR PAGINASSSSSS

##import PyPDF2
##minutesFile=open("meetingminutes.pdf","rb")
##pdfReader = PyPDF2.PdfFileReader(minutesFile)
##page=pdfReader.getPage(0)
##page.rotateClockwise(90)
##
##pdfWriter=PyPDF2.PdfFileWriter()
##pdfWriter.addPage(page)
##resultPdfFile=open("roratedPage.pdf","wb")
##pdfWriter.write(resultPdfFile)
##resultPdfFile.close()
##minutesFile.close()


################################################################################

 #####################Encrypting PDF

##import PyPDF2
##pdfFile=open("meetingminutes.pdf","rb")
##pdfReader=PyPDF2.PdfFileReader(pdfFile)
##pdfWriter=PyPDF2.PdfFileWriter()
##for pageNum in range(pdfReader.numPages):
##    pdfWriter.addPage(pdfReader.getPage(pageNum))
##
##pdfWriter.encrypt("swordfish")
##resultPdf=open("encryptedminutes.pdf","wb")
##pdfWriter.write(resultPdf)
##resultPdf.close()


##############################

###PROJECT COMBINING SELECT PAGES FROM MANY PDFS

##Find all pdf files in the current working directory
## sort the filenames so the PDF are added in order.
##Write each page.excluding the first page of each PDF to the outpt file.

####we need to make that

#call os.listdir() to find all the files in the working directory and remove any non-PDF file

#call python sort () list method to alphabetize the filenames
#create a pdfilewriter object for the output pdf
#loop over each pdf file.creating a pdffilereader object for it
#loop over each page(except the first) in each pdf file.
#add the pages to the output pdf
#write the output pdf to a file named allminutes.pdf

#####step 1 find all pdf files

##import PyPDF2, os
##
###Get all the PDF filenames.
##pdfFiles=[]
##for filename in os.listdir(r"."):
##    if filename.endswith(".pdf"):
##        pdfFiles.append(filename)
##        #print(filename)   # encuentra todos los pdf en la zona
##        #print(pdfFiles[0])   # ya estan dentro de la matriz
##
##
##pdfFiles.sort(key= str.lower)
##
##pdfWriter = PyPDF2.PdfFileWriter()
##
###TODO: Loop throught all the PDF files.
###print(filename)
##for filename in pdfFiles:
##    pdfFileObj = open(filename, 'rb')
##    pdfReader = PyPDF2.PdfFileReader(pdfFileObj)
##
##
###TODO: Loop throught all the pages ( except the first) and add them.
##
##    for pageNum in range(1, pdfReader.numPages):
##        pageObj = pdfReader.getPage(pageNum)
##        pdfWriter.addPage(pageObj)
##
###TODO: Save the resulting PDF to a file
##
##
##pdfOutput=open("allminutes.pdf","wb")
##
##pdfWriter.write(pdfOutput)
##pdfOutput.close()
##


#########################################

