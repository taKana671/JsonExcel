# JsonExcel

Export JSON-format data to Excel like RDB or the exported data in Excel to JSON file.


![spec](https://user-images.githubusercontent.com/48859041/101023648-67febd80-35b6-11eb-9e06-b6146aef7c04.png)


# Requirements

* Python 3.8
* openpyxl
* xlsxwriter


# Environment

* Windows10


# Usage

 ### *class* ToExcel(path)
 
  * Export JSON-format data to Excel like RDB
  
  ```bash
  from jsonexcel import ToExcel
  
  to_excel = ToExcel(path)                                    # path: JSON file path
  to_excel.convert()                                          # When export all data
  to_excel.partial_convert(column name 1, column name 2, ...) # When export selected data
                                                              # if json_data is {'aa': 1, 'bb': {'cc': 2, 'dd': [1, 2, 3, 4]}},  
                                                              #    column name is like 'aa', 'bb.cc', 'bb.dd'. 
  ```
  
  ### *class* FromExcel(path)
  
   * Exported data in Excel to JSON file. 
   * The Excel must be the file output with convert method of ToExcel class.  
   
   ```bash
   from jsonexcel import FromExcel
   
   from_excel = FromExcel(path)                                  # path: Excel file path
   from_excel.convert()                                          # Export data to JSON file
   from_excel.convert(
       indent=4,                                                 # If you need indent on JSON file, specify number.
       replacement={'apps.app_id': 'app-id, 'price': 'prices'}   # If you need to change key name, specify dict
    )                                                        
   ```
   
  # Converter Tool
  
  
![converter_demo](https://user-images.githubusercontent.com/48859041/102998457-8713be00-456a-11eb-8899-10b9f3399c22.gif)


  ```bash
  >>>python converter.py
  ```


  # Note
  
   * If hyphens(-) or dots(.) are found in keys in a JSON file, they are replaced with underbar(\_) before export to Excel file.
   * When exporting data in Excel to JSON file, specify replacement if you want to change keys in which hyphens or dots were replaced with underbar.
  
