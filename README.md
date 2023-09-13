# Data-cleaning-and-EDA
This repository contains the file in which i have performed data cleaning techniques on a web scrapped data and than performed EDA

## Data Assessing and Cleaning

### Quality Issues

1. **model** - some brands are written diiferently like OPPO in model column `consistency`
2. **price** - has unneccesary '₹' `validity`
3. **price** - has ',' between numbers `validity`
4. **price** - phone Namotel has a price of 99 `accuracy`
5. **ratings** - missing values `completeness`
6. **processor** - has some incorrect values for some samsung phones(row # -642,647,649,659,667,701,750,759,819,859,883,884,919,927,929,932,1002) `validity`
7. There is ipod on row 756 `validity`
8. **memory** - incorrect values in rows (441,485,534,553,584,610,613,642,647,649,659,667,701,750,759,819,859,884,919,927,929,932,990,1002) `validity`
9. **battery** - incorrect values in rows(113,151,309,365,378,441,450,553,584,610,613,630,642,647,649,659,667,701,750,756,759,764,819,855,859,884,915,916,927,929,932,990,1002) `validity`
10. **display** - sometimes frequency is not available `completeness`
11. **display** - incorrect values in rows(378,441,450,553,584,610,613,630,642,647,649,659,667,701,750,759,764,819,859,884,915,916,927,929,932,990,1002) `validity`
12. certain phones are foldable and the info is scattered `validity`
13. **camera** - words like Dual, Triple and Quad are used to represent number of cameras and front and rear cameras are separated by '&'
14. **camera** - problem with rows (100,113,151,157,161,238,273,308,309,323,324,365,367,378,394,441,450,484,506,534,553,571,572,575,584,610,613,615,630,642,647,649,659,667,684,687,705,711,723,728,750,756,759,764,792,819,846,854,855,858,883,884,896,915,916,927,929,932,945,956,990,995,1002,1016
) `validity`
15. **card** - sometimes contains info about os and camera `validity`
16. **os** - sometimes contains info about bluetooth and fm radio `validity`
17. **os** - issue with rows (324,378) `validity`
18. **os** - sometimes contains os version name like lollipop `consistency`
19. missing values in camera, card and os `completeness`
20. datatype  of price and rating is incorrect `validity`



### Tidiness Issues

1. **sim** - can be split into 3 cols has_5g, has_NFC, has_IR_Blaster
2. **ram** - can be split into 2 cols RAM and ROM
3. **processor** - can be split into processor name, cores and cpu speed.
4. **battery** - can be split into battery capacity, fast_charging_available
5. **display** - can be split into size, resolution_width, resolution_height and frequency
6. **camera** - can be split into front and rear camera
7. **card** - can be split into supported, extended_upto


# Exploratory Data Analysis
# `Univariate analysis`
* Categorical column
* Numerical column

**Findings**
Here we can see that price column is highly positively skewed which is not good for from analysis pov because some of the statistical model will not run properly. so we to sort this out before moving to the next column. After analysing we found that 4 devices are premium devices material like GOLD has been used on this because of which the price is high such devices would not add up in our analysis so we are dropping them. Lets check the skewness of the data before and after removing outliers.
* Initial skewness: `7.27`
* skewness after removing outlieres: `2.40`

* Lets analyse the next column `rating`
* `Findings`
This particular column is negatively skewed and don't have any outliers but it contains 89 missing values which has to be treated

* Let's analyse the next three categorical columns 
* `has_5g, has_nfc, has_ir_baster`
- `Findings` 
- 56% of the devices are 5G unabled
- 39.7% have nfc
- only 16.7% devices are ir_blaster unabled

- Let's analyse the next column `processor_brand`
- `Findings`
- There are 9 processor's which have total count less then 6. so let's treat them and put on a category called other before analysing the column
- `Snapdragon` has highest marked share `42.3%` followed by `helio 21.3%` then dimensity `18.7%`

- Let's analyse the  column `processor_speed`
- `Findings`
- mean processor speed is `2.43` and this column don't contain's any outliers and data is also skewed

* Let's analyise the next columns
* `internal_ram & internal_memory`
- `Findings`
- There are 4 devices which have ram above 16 because of which the skewness of the data is `7.23` after replacing values with 16 we got the skewness of `0.740`
- 8GB is the most common ram having `34.7%` followed by `6GB 24.4%` then `4GB 22%`
- Internal memory column has 2 missing values
- 128GB is the most common internal storage having `54.5%` followed by `64GB 19.3%` then `256GB 16.4%`

* Lets analyze `screen_size` column
- mean screen size in our data is `6.53` and skewness is also `-2.239` which means that this particular column is negatively skewed.

* Lets analyze `refresh_rate` column
- `55.6%` of the devices has 120Hz refresh rate followed by `90Hz in 36.6%` then `144Hz in 6.5%`. Skewness of the data is 0.7 so we keep the outlier values as of now will treat on later stage if required

* Lets analyze `battery_mAh` column
- There are 3 devices which have battery greater than 7500 and 2 of them above 20k so we have dropped both these columns
  
* Lets analyze `os` column
- There are 8 devices which are of same os but bit different names we have updated all the to a single name.
- 95% of the contribution is of android devices

# **Bivariate Analaysis**
The agenda of our analysis is finding the relation between the price columns and other columns
- `Brand_name & price`
- After analysisng we found out that avg price of apple smartphones are highest, followed by google then samsung,oneplus
* `has_5g, has_nfc, has_ir_baster`
* has5g & has_nfc has direct co-relation with the price column. If a device contains both these feature then the price would be on higher side whereas the presence of ir_blaster does't contribute that much
- `processor_brand & process_speed`
- processor brand and speed are directly coorelated with the price. Higher the speed higher the price. 
- snapdragon,dimensity and bionic make processor with speed above 3.0GHz
- unisoc don't make processors above 2.0 GHz of speed

