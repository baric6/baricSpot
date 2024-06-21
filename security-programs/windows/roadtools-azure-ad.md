# Roadtools azure ad

ROADrecon is a tool for exploring information in Azure AD from both a Red Team and Blue Team perspective. In short, this is what it does:

* ```
  Uses an automatically generated metadata model to create an SQLAlchemy backed database on disk.
  ```
* ```
  Use asynchronous HTTP calls in Python to dump all available information in the Azure AD graph to this database.
  ```
* ```
  Provide plugins to query this database and output it to a useful format.
  ```
* ```
  Provide an extensive interface built in Angular that queries the offline database directly for its analysis.
  ```

ROADrecon uses async Python features and is only compatible with Python 3.6-3.8 (development is done with Python 3.8).

Download

{% embed url="https://github.com/dirkjanm/ROADtools" %}
