ETL into SalesForce

The goal of this project is to Extract Data from a MYSQL database, Transform the data as to ensure that it Lands correctly in SalesForce. In this MYSQL dataset, there are 3 primary keys, Class, Student and Staff, that must be linked to the corresponding foreign keys, so the process will be repeated 3 times.


After importing the dependencies, the first goal is to create an engine and connect to the MYSQL database. Then the data needed is extracted using read_sql. The data is then transformed into a list of dictionaries using to_dict. 

A SalesForce record is created by looping through the dictionary list and creating a new iterrated dictionary called 'record' that is landed into SalesForce using a try/except. 

Once the primary key is landed in SalesForce, an empty list is created. Then we run a sf.query_all_iter from the SalesForce table that has just been created. The crux of the exercise and the next step here is to re-extract the necessary columns, including the ID number given by SalesForce to each 'record' once it landed. With these columns identified, we then extract the Class Table from the MySQL database. Because Course and Class both have 'ID_Course' as column, they can now be left merged. The class table now has the unique SF ID and once the 'Start Date' and 'End Date' Columns are converted to dates. The modified Class Table  table will now land in SalesForce and will be successfully linked to the Primary Course Table. Repeat these steps 2 more times for Staff/Staff Assignment & Student / Class Participant.

![Image of Class](https://lh3.googleusercontent.com/E_KwIq6I0e-B6q1rGDXRS9OuyqdU4UMLWbtxBcaj91vWPlDa3t5cCqC7sKRE4RqIv2IhhPaxZpoWua_FNwG5xgMbaAbKjCbAc5zpYPizqZOaRQYrXWpbg9pLC153sXPO7eehmy2EncciIno1ralm47NSEb4o0Zm1IjcWtvlx66sfXT4juwb6cIz2xtm0qKRFxW9ktcbywlcSDuYlVFEHjON7wP9CR7zcd1pwSWEI_olaJv4qbrb781F2DHNYkZHsjaGrZpHWsKk2UTvuo3wwZVxP_esCJs_spYy_FaUdShh_1og-CuaB8l785kCjSTnDU7PJO6lnXsCvUyBYhTJLEi4kb5cSeQLxZhk-cooMPZZCHlcDquDIyeCMc6Q0D7heAHa4EH_dHdyPV2jv1oHuNZwjpq5URJXJ52cyzhr-F0lZnb2IFoKI5IvUbQ3mA0kgk77k3y54KXqJ6Zie6GYoHqBiRFrdatyQygzw0m87kTL3IjBGB3mdKErzzx4ti5kZ67033A02jsfxj9vLRlWh_QaCEKbghpph_VPaYuNC4K4JLLoVzpyKJ88qXQ5J3slZ621TLJle8cPvw1R1CF4ywbfMfsTZP2Yb3wkedr9aLSoVPFsWvisGIsp3tiutb7FTKVLUNFv31PxHmcaYez1X2pKmXintZ0x8aKVmy_MARSkiWfxYY2oE73SSAKON=w1871-h380-no?authuser=0)

![Image of Course](https://lh3.googleusercontent.com/o7gOg9p-8GLv4grO_6iYme9TdB_9nIiBTNbMNU_x0Qo6wF9wct1Q9UaxvFwf_A3NGh-huIFy_BzZohXqN1Hcgr243iZWMn2wskwHZy5wJRklrhd2jgEo_r4lM9nS7NquZ7Oy21IHyxxiEFX8PuBiXy73cbeAWCDCaHYzymdmWj92Gtb3DsfzM13VZhbm1hwvlreErxD1a7f9QJjgAc_Ua_9HmAIso7Mypbv6PaTinu5Lm-PcVf2XCjGquT3JrQbgf96qtTf4xrh6diLLMdk7oqlKSC-UfFyWHXivJC4nyt_-ox4eQE5eLRKIbft1ajer5y-EXJbOj1K7ADbnWsxgKGPAy0Y_zSa4V6jD-IetsLcFSuG3GMjNZtubasNIO4QOLgQKgZVpbmmZSo4GUoGh4rYgynTqqoZa5j10_4IX3vSgiy2oDuQIHtS30_kDFeBP2SbOsLo2n9sOz1DrLJuvFy4PZTgWgGXxWAQ14rmd-U-d6UBG7iQN3zAUidp6vjZEqb0m_M3fZLuLhuydUCHVY7v1gsMvLLgFgirIYtV1PGOmk9drSP11VkLnJHmfK8oaOIk6js7SCJGiWyaMrdMlm2I4FLgL2yj_Y_BJxPTXWAIoY-TnNT4c09o7YVXJKdEsa6rs_zWEuEHWoGeaXdOIpt9MIs2d159xqDNqx_0RPzqVKs2BSQ9ZzpAOrool=w1864-h568-no?authuser=0)

