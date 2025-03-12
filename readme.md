# Install

```zsh

mkdir -p ~/.bin
cp ask ~/.bin/.
echo 'export PATH="$PATH:${HOME}/.bin"' >> ~/.zprofile
echo "export GOOGLE_API_KEY=<YOUR API KEY>" >> ~/.zprofile
. ~/.zprofile
```

## Example use cases

### Simple Question and Reponse
$ ask "what is the first day of week?" <br>
Monday

### Creating Scripts
$ ask "write a shell script to output name and File Access Date/Time using exiftool given a directory of images as an option" > list_images.sh
$ chmod 755 list_images.sh
$ ./list_images.sh test_images
91036491.png: 2024:08:16 13:18:35-05:00

### For the Ultra Brave Running a Command Blindly
$ $(ask "macos terminal command for listing directory contents")
ask		readme.md	test

### Getting Directions
$ ask "how do I make jello" --markdown --glow

```
    GENERATED CONTENT                                                                                                 
  ─────────────────────                                                                                               
    Ingredients:                                                                                                      
                                                                                                                      
  • 1 (6 ounce) package cherry gelatin mix                                                                            
  • 1 cup boiling water                                                                                               
  • 1 cup cold water                                                                                                  
  • 1 (15 ounce) can pitted dark sweet cherries, drained                                                              
                                                                                                                    
  Instructions:                                                                                                       
                                                                                                                    
  1. Prepare the gelatin: In a medium bowl, whisk together the gelatin mix and boiling water until the gelatin is     
  dissolved.                                                                                                          
  2. Add cold water: Stir in the cold water.                                                                          
  3. Add cherries: Gradually fold in the drained cherries.                                                            
  4. Pour into mold: Pour the gelatin mixture into an 8-inch square baking dish or individual molds.                  
  5. Refrigerate: Refrigerate for at least 4 hours, or until firm.                                                    
  6. Unmold: To unmold, dip the baking dish briefly in hot water. Invert the jello onto a serving plate.              
                                                                                                                    
  Tips:                                                                                                               
                                                                                                                    
  • For a firmer jello, use 1 1/2 cups of cold water.                                                                 
  • To make the jello more flavorful, add a few drops of cherry extract to the gelatin mixture.                       
  • For a layered jello, alternate layers of cherry jello with vanilla or other flavors.                              
  • To make cherry jello shots, pour the gelatin mixture into individual shot glasses.                                
  • Serve the jello with whipped cream or ice cream.    |                                                             
                                                                                                                    
             SAFETY RATINGS                                                                                           
  ────────────────────────────────────                                                                                
    HARM_CATEGORY_SEXUALLY_EXPLICIT:                                                                                  
    NEGLIGIBLE                                                                                                        
    HARM_CATEGORY_HATE_SPEECH:                                                                                        
    NEGLIGIBLE                                                                                                        
    HARM_CATEGORY_HARASSMENT:                                                                                         
    NEGLIGIBLE                                                                                                        
    HARM_CATEGORY_DANGEROUS_CONTENT:                                                                                  
    NEGLIGIBLE              
```
