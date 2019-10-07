# study_DataFrame
---
## study01. 
### DataFrame内のあるフィールドに設定された要素の種類ごとにレコードを抽出し、行と列を入れ替えて新しいDataFrameを生成する。
  - CSV読み込み。`.read_csv`
  - 日時のデータが入っているフィールドをDateTime型に変換。`.to_datetime`
  - DateTimeのフォーマットを変更。`dt.strftime('%m-%d')`
  - あるフィールドの要素ごとに、データ抽出。`.groupby`、`for idx, df_select in df_grp.groupby(level=[0]):`
  - 行列を入れ替えて新しくDataFrameを生成。
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/01-1_Base_DataFrame.png" height="200">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/01-2_Grouped_DataFrame.png"  height="200">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/01-3_adjusted_DataFrame.png"  height="200">
    
  - 積み上げグラフを生成。`.plot(kind='bar'・・・`
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/01-4_stacked_barchart.png" width="400">
  
  
  

  
