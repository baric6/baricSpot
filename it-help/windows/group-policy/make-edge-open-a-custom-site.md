# Make Edge open a custom site

1. open group policy management&#x20;
2. navigate to:&#x20;
   1. forest -> Domains -> \<your domain>&#x20;
3. Select or create a policy you want to change&#x20;
4. double click on the policy&#x20;
5. group policy editor will open up
6. under User configuration&#x20;
   1. policies -> Admin templates -> Microsoft edge -> select the policy "Startup, home page and new tab"
   2. enable the following policies
      1. Config the home page URL : _URL you want to open_
      2. Action to take on startup&#x20;
      3. Sites that open when browser starts&#x20;
      4. Show home button tool bar : _Adds home button to bar_
7. On windows device run in CMD:
   1. gpupdate /force
   2. gpresult /r
8. if that don't work restart your PC
9. Open up edge and it should open to your site (may take some time to sync over)
