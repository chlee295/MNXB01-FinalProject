# MNXB01-FinalProject
Final Project for the course MNXB01 at Lund University 2022.
The draft report is the file "draftReport.pdf", placed both in the top directory and in the "Latex" directory.
--------------------------------
How to Generate Philip's Plots
-------------------------------
To make sure that everything works, use Ubuntu 20 and run
"source /localRoot/rootUbuntu20/bin/thisroot.sh"
to make sure root is running properly. Then, cd into the directory "PhilipCode". There, run 
"make all" in the terminal to generate datafiles starting with "hotCold-" and "summerStart-" necessary for the root plots.
Then, copy and paste these files into the directory "rootmacros". 

After this, type "root" in the terminal to begin using root. In root, run 

".L rootmacros/hot.C+",

".L rootmacros/cold.C+" and

".L rootmacros/summer.C+"

to load the functions "hot()", "cold()" and "summer()". Running these functions will create the used plots.


Please note that using Aurora's root (and c++) versions may cause issues. It has been found that things like using strings,
accessing elements in vectors and using for loops in the style of "for (auto i: myvector) {}" can cause issues with both 
root for some things and with c++ for other things (with code working fine outside of Aurora complaining about things in the 
standard library missing).



---------------------------------
How to Run Chris's code
---------------------------------
In order to make the histogram, i have use of the excel and root. Firstly, I use the finding function in excel to locate the string or the data I need. However, it is in a string format, and i need to separate the temperature data from the string. Hence i make use of the data analysis function in excel. It can seprate the string by detecting each of the symbol(such as ;,) in the string. As a result i can seprate the temperature data I need from the original excel file.After that I use Win Zip to transfer the revised data to Auora. For the coding part, I create a new canvas named as c1 and with the title of Temperature of Umeå FLyplats. Since I want to show the two graphs in the same page and in parllel, so i make use of the function of Divide(2,1).After that, i use the public member function of TH1 which can be used to create a 1-d histogram with variable bins type of numbers.I create a histogram named as hist with the x,y axis be [°c], and Entries respectively. And the pixels of the histogram is set to 700. Besdies, the range of x axis is from -30 to 40. Then, I try to operate and open  the data file which named as 8-23Temp.txt into the histogram by using the command ifstream and open. The data should be store in a ifstream called infiles. After that i create a new variable named as tmp by using the command double. In order to make sure the data keep on filling untill all data are input to the histogram, i make a while statment. While there is unused data in the infiles, it will always run the loop, and fill into the histogram.Lastly, I try to use  the command SetFillColor to control the color of the graph. Besides, i also create variable of mean and stdv to store the standard deviation and the mean of the graph.

The similar strategy i used to create another graph. However i will change back the visulizing data process by using some function in the root but not in the Excel. 





-------------------------
 {TH1I* hist = new TH1I("hist", "Temperature of 23/8 from 1962 to 2020;[#circC];Entries", 500, -3.2, 40);
ifstream infile;
infile.open("8-23Temp.txt");
double tmp;
while (infile>>tmp) {hist->Fill(tmp);}
hist->SetFillColor(kRed + 1);

double mean = hist->GetMean(); //The mean of the distribution
double stdev = hist->GetRMS(); //The standard deviation
TCanvas* can = new TCanvas();
hist->Draw();}
