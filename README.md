
![Logo](https://www.howtogeek.com/wp-content/uploads/2021/08/ShareAsViewer-GoogleDocsViewOnly.png?trim=1,1&bg-color=000&pad=1,1)

# How to Download View Only Google Drive Files?

Google Drive is a popular cloud storage service that allows you to store and share files with others. However, sometimes you may come across a situation where you need to download a view-only Google Drive file. A view-only file is a file that you can only view but not edit or download. In this tutorial, we will show you how to download view-only Google Drive files.

I had some documents that I couldn't read on my Android phone or iPad because they were in read-only mode, and these mobile devices couldn't handle it. I wanted to be able to read these documents on other devices besides my PC, so I came up with a little "hack" in JavaScript.

Please note that this method was tested on the Chrome browser. Also, this method converts the pages to JPG images, although it may be possible to preserve the text instead. However, I did not have the time to explore this further, and the JPG solution was sufficient for my needs.

If you only see a part of the document visible after running the script, try zooming out your browser first, and then run the script.

## Here are the step-by-step instructions on how to use this method:

1. Open the document in Google Docs.
2. Scroll down to the bottom of the document so that all the pages are present on the screen.
3. Open Developer Tools in a separate window, and select the Console tab.
4. Copy the code and paste it into the Console tab.
5. Press enter to execute the code.
6. Once you have completed these steps, you should be able to perform the desired action.


## Usage

```python
let jspdf = document.createElement("script");
 
jspdf.onload = function () {
 
    let pdf = new jsPDF();
    let elements = document.getElementsByTagName("img");
    for (let i in elements) {
        let img = elements[i];
        console.log("add img ", img);
        if (!/^blob:/.test(img.src)) {
            console.log("invalid src");
            continue;
        }
        let can = document.createElement('canvas');
        let con = can.getContext("2d");
        can.width = img.width;
        can.height = img.height;
        con.drawImage(img, 0, 0, img.width, img.height);
        let imgData = can.toDataURL("image/jpeg", 1.0);
        pdf.addImage(imgData, 'JPEG', 0, 0);
        pdf.addPage();
    }
 
    pdf.save("download.pdf");
};
 
jspdf.src = 'https'+'://'+'cdnjs'+'.cloudflare'+'.com/ajax/libs/jspdf/1.5.3/jspdf.debug.js'; /* had to set it like this, because disqus was breaking the link.. */
document.body.appendChild(jspdf);
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate.
