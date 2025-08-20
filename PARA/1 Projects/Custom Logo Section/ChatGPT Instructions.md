
So I now need to add a new section where the user will need to first select a template that defines a design that can be included with the text for the embroidery. - Logo and Text, Design Only or Text Only...  Each template can also have the option of one or two or 3 lines of text added to the design. So if they select a template that contains two lines of text then the Text section should show 2 lines of text the user could enter. If the select a template with 1 line of text it will display1 line.  This new section should be at the top and dictates how the Text section should look - one or two lines of text. Could you add this new section. The PulseID to retrieve a list of templates is /api/Templates/ListTemplates/ and needs to be called to list the available templates. Also need to filter the list of template where the code starts with RBG_. Also instead of displaying the template name I want to reference a url to an image. To get the template image url i need to call api/Templates/GetThumbnail/?id=RBG_Three_Line_Template api to get this url for every template. This is similar to how the list of font images are displayed.


![[Pasted image 20250812200443.png]]
Here is a snapshot of the latest version of my widget designer. The next thing I want to do is initialize the Text boxes, Font selection and Color selection base on the Template that is selected. For example if RBG_Image_With_Top_Text_Template is selected then There should be only one text box and it should be initialized with selectedTemplate text value. The selectedTemplate object contains a json array of elements called TemplateElements that contain elements that contain what Text content, Font, and color to use. I would like to use this to initialize control sections. Below is what json elements to use from the Template Elements..

templateElement.Text - Contains the text to populate text boxes with.
templateElement.TextColour - What to initialize the color control with.
templateElement.FontOverride - What to initialize the font control with.

Can you update my code to initialize the Text box, Font control and Color control with this.

-------------

Now that I have  SPA for this widget I will now need to use this widget within the BigCommerce website for rockbottomgolf. I am going to need a "Customize Me" button on the Product view page that will go to a new page with the BigCommerce/RockBottomGolf.com theme but with my SPA widget code writing out to a container within the BigCommerce theme. Currently for the canned PulseID widget the following is included to enable this - <script src="https://rockbottom.pulseidconnect.com/widgetbcrockbottomff/bigcommerce.js?v=1" ></script>. I will nee to include a similar thing. When the product page is shown I will need to display the "Customize Me" button in the bigcommerce container. Any tips on how I could do this.

I need to add a new controls section with the label "Designs:" that should be after the "Template:" section. This will should be a horizontally scrollable list of designs retrieved using the api - /api/Designs/GetDesigns/. Each design returned has a DesignPreviewURL that can be used for displaying the design image. This can be handled similar to fonts and the FontPreviewUrl property used in the FontSelector. This new "Designs" control should have arrows to the left and right allowing to scroll the images and be independent scrolling. I have attached a screenshot. Also the current design being used should be pre-selected.

const tr = await fetch(`${apiBase}?endpoint=/api/Templates/GetThumbnail&id=${encodeURIComponent(code)}`);


 think the GetThumbnail for Designs has to be done the same way as the Template Control where it uses getTemplateThumbnail during the fetchTemplates.
