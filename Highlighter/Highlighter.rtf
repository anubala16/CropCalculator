'''
Created on Apr 18, 2017
CropCalculator 
Hightlighter.py Gets a few facts of "interest" for crops; 
interest = measured according to various dictionaries and statistics :)   
@author: Anusha Balaji (abalaji)
@author: Brian Clee (bpclee)
@author: Xiangqing Ding (xding3) 
@author: Shruti Rai (srai)
@author: Danny Streeter-Jimeno (djstreet)
'''

import re
#nltk.download("punkt")

loc_dict = [] # dictionary of location terms (from locations.txt) 
econ_dict = [] # dictionary of economic terms (from economics.txt)
ecol_dict = [] # dictionary of ecology terms (from ecology.txt)
crop_dict = [] # dictionary of crops (from crops.txt)

# Bunch of counters to keep track of "interesting" facts about each crop
cropStatCounter = 0 # how many facts have #s in them? 
cropLocCounter = 0 # how many facts with location in them? 
cropEconCounter = 0 # how many facts with some economic activity in them? "produced", "sold", "harvested" etc.  
cropEcolCounter = 0 # how many facts with some crop ecology in them? 

sentences = [] # 2-d array of sentences for each crop, based on the cropData text file 
facts = [] # 2-d array of facts for each crop 
unusedSentences = [] # non-facts/extra sentences from the crop text files 


'''
program's controller/director; transfers control to main function
and returns the facts! 
'''
def getFacts() :
    main()
    global facts
    return facts

'''
populates the dictionaries, finds interesting facts for each of the crops
stores the results in facts [] 
'''
def main(): 
    #------ populate locations -------- 
    
    locFile = open('./docs/DataFiles/locations.txt', "r")
    locFileLines = locFile.readlines()
    numOfEntries = len(locFileLines)
    for i in range (0, numOfEntries) : 
        loc_dict.append(locFileLines[i].strip())
    locFile.close()
    
    #----------- populate economics terms-------  
    
    econFile = open('./docs/DataFiles/economics.txt', "r")
    econFileLines = econFile.readlines()
    numOfEntries = len(econFileLines)
    for i in range (0, numOfEntries) : 
        econ_dict.append(econFileLines[i].strip())
    econFile.close()
    
    #----------- populate ecological terms------ 
    
    ecolFile = open('./docs/DataFiles/ecology.txt', "r")
    ecolFileLines = ecolFile.readlines()
    numOfEntries = len(ecolFileLines)
    for i in range (0, numOfEntries) : 
        ecol_dict.append(ecolFileLines[i].strip())
    ecolFile.close()
    
    #----------- populate crops dict------ 
    
    cropFile = open('./docs/DataFiles/crops.txt', "r")
    cropFileLines = cropFile.readlines()
    numOfEntries = len(cropFileLines)
    for i in range (0, numOfEntries) : 
        crop_dict.append(cropFileLines[i].strip())
    cropFile.close()
    
    # open each crop file and gather data on each crop 
    for cropNo in range(0, len(crop_dict)) : 
        curCropFileName = "./docs/DataFiles/CropData/" + crop_dict[cropNo] + ".txt"
        
       # curCropFileName = "./CropData/" + crop_dict[cropNo] + ".txt"
        with open(curCropFileName, "r") as in_file:
            text = in_file.read()
            #.decode("utf-8")
            crop_Sentences = re.split(r'(?<!\w\.\w.)(?<![A-Z][a-z]\.)(?<=\.|\?)\s', text)
            
            global sentences
            sentences.append(crop_Sentences)
            
            # Reset the counter variables for this crop :) 
            global cropStatCounter
            cropStatCounter = 0
            global cropLocCounter
            cropLocCounter = 0 
            global cropEconCounter
            cropEconCounter = 0 
            global cropEcolCounter
            cropEcolCounter = 0  
            
            global facts
            facts.append([])
            global unusedSentences
            unusedSentences.append([])
            findInterestingFacts(cropNo) 
            if (len(facts[cropNo]) < 7) : # yikes, we don't even have 5 interesting facts! 
                findFewFacts(cropNo, 7-len(facts[cropNo]))
            in_file.close()
            facts[cropNo].sort()
            
            for i in range (0, len(facts[cropNo])) :
                facts[cropNo][i] = facts[cropNo][i][4:] 
        
    generateOutput()
    #printFacts()
        
'''
Testing function 
print the facts! 
'''
def printFacts(): 
    print("\n***********\nFinal Results: \n***********\n")
    for j in range (0, len(facts)) : 
        print (crop_dict[j] + "\n----")
        for k in range (0, len(facts[j])) : 
            print("\\d . ", k, facts[j][k])
        print("________\n") 
    

'''
Helper function 
called only once per crop :) 
Appends to the fact list when it finds an "interesting" fact 
@param sentences from the crop text file
@param cropFacts result set of the crop 
@param extraSentences non-interesting facts and unused sentences from the file 
'''
def findInterestingFacts(cropNo):
    # what kind of facts do we need??
    needStats = True
    needLocFact = True
    needEconFact = True
    needEcolFact = True
    
    sent_count = len(sentences[cropNo])
    for i in range(0, sent_count) : 
        # Do we need more facts? If so, what kind?? 
        if (needStats == True and cropStatCounter >= 2) : 
            needStats = False
        if (needLocFact == True and cropLocCounter >= 1) : 
            needLocFact = False 
        if (needEconFact == True and cropEconCounter >= 1) :
            needEconFact = False
        if (needEcolFact == True and cropEcolCounter >= 3) : 
            needEcolFact = False
        
         # if we have all the facts, we're done!     
        if (needStats == False and needLocFact == False and needEconFact == False and needEcolFact == False) : 
            break
        
        toAdd = isSentenceUseful(needStats, needLocFact, needEconFact, needEcolFact, sentences[cropNo][i].lower())
        if (toAdd == 1) : 
            facts[cropNo].append("Stat" + sentences[cropNo][i].strip())
        elif (toAdd == 2) : 
            facts[cropNo].append("Loca" + sentences[cropNo][i].strip())
        elif (toAdd == 3) : 
            facts[cropNo].append("Econ" + sentences[cropNo][i].strip())
        elif (toAdd == 4) : 
            facts[cropNo].append("Ecol" + sentences[cropNo][i].strip())
        else : # 0
            unusedSentences[cropNo].append(sentences[cropNo][i].strip())

'''
Helper function 
Should the sentence be added to the crop's fact list? 
@param needStats - true if we still need a fact with #, false otherwise 
@param needLocFact - true if we still need a fact with a term from the location dict, false otherwise 
@param needEconFact - true if we still need a fact with a term from the Economics dict, false otherwise 
@param needEcolFact - true if we still need a fact with a term from the Ecology dict, false otherwise 
@param sentenceToTest - sentence to check for usefulness 
@return True if sentenceToTest is an "interesting" fact and false otherwise 
'''
def isSentenceUseful(needStats, needLocFact, needEconFact, needEcolFact, sentenceToTest): 
    
    if (needStats) : 
        # if this is a "good" sentence, update global counter and return 
        hasNum = any(char.isdigit() for char in sentenceToTest)
        if (hasNum == True) : 
            global cropStatCounter
            cropStatCounter += 1 
            return True
        # else, continue :) 
        
    if (needLocFact) : 
        # if this is a "good" sentence, update global counter and return 
        loc_Count = len(loc_dict)
        temp = False
        for index in range(0, loc_Count) : 
            if (loc_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropLocCounter
            cropLocCounter += 1 
            return True
        # else, continue :) 
        
    if (needEconFact) : 
        # if this is a "good" sentence, update global counter and return 
        econ_Count = len(econ_dict)
        temp = False
        for index in range(0, econ_Count) : 
            if (econ_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropEconCounter
            cropEconCounter += 1 
            return True
        # else, continue :) 
        
    if (needEcolFact) : 
        # if this is a "good" sentence, update global counter and return 
        ecol_Count = len(ecol_dict)
        temp = False
        for index in range(0, ecol_Count) : 
            if (ecol_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropEcolCounter 
            cropEcolCounter += 1 
            return True      
    return False
def isSentenceUseful(needStats, needLocFact, needEconFact, needEcolFact, sentenceToTest): 
    
    if (needStats) : 
        # if this is a "good" sentence, update global counter and return 
        hasNum = any(char.isdigit() for char in sentenceToTest)
        if (hasNum == True) : 
            global cropStatCounter
            cropStatCounter += 1 
            return 1
        # else, continue :) 
        
    if (needLocFact) : 
        # if this is a "good" sentence, update global counter and return 
        loc_Count = len(loc_dict)
        temp = False
        for index in range(0, loc_Count) : 
            if (loc_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropLocCounter
            cropLocCounter += 1 
            return 2
        # else, continue :) 
        
    if (needEconFact) : 
        # if this is a "good" sentence, update global counter and return 
        econ_Count = len(econ_dict)
        temp = False
        for index in range(0, econ_Count) : 
            if (econ_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropEconCounter
            cropEconCounter += 1 
            return 3
        # else, continue :) 
        
    if (needEcolFact) : 
        # if this is a "good" sentence, update global counter and return 
        ecol_Count = len(ecol_dict)
        temp = False
        for index in range(0, ecol_Count) : 
            if (ecol_dict[index].lower() in sentenceToTest) : 
                temp = True
                break
        if ( temp == True ) : 
            global cropEcolCounter 
            cropEcolCounter += 1 
            return 4      
    return 0

'''
Helper function 
Finds "howMany" sentences with 'crop' in them and appends to crop's fact list. 

@param crop: name of the crop
@param sentences: sentences not yet used from the cropData file 
@param cropFacts: fact set for this crop
@param howMany: number of "facts"/sentences to find with crop name in them
'''
def findFewFacts(cropNo, howMany) : 
    crop_sentences = unusedSentences[cropNo]
    sent_count = len(crop_sentences)
    cropName = crop_dict[cropNo].lower()
    for i in range(0, sent_count) : 
        if (howMany == 0) : 
            break
        
        curSent = crop_sentences[i].lower()
        if (cropName in curSent) : 
            howMany -= 1
            facts[cropNo].append("ZZZZ" + crop_sentences[i].strip())

'''
Writes the facts to each crop's fact file :)
'''
def generateOutput(): 
    # print(crop_dict)
    for i in range(0, len(crop_dict)) : 
        getMyFacts(crop_dict[i])
    
'''
Helper function 
writes the given crop's facts to its corresponding output file 
@param cropName crop whose facts must be written to its output file 
'''
def getMyFacts(cropName): 
    index = crop_dict.index(cropName)
    this_crop_facts = facts[index]
    outputFile = open("Facts_" + cropName + ".txt", "w")
    for i in range (0, len(this_crop_facts)) : 
        outputFile.write(this_crop_facts[i].strip())
        outputFile.write("\n\n")
    outputFile.close()

'''
Starter!
'''
if __name__ == "__main__":
    main()
