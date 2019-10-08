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
    
  - 積み上げグラフを生成。`.plot(kind='bar', stacked=True,・・・`
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/01-4_stacked_barchart.png" width="400">
  
---
## study02. 
## DataFrame内を行方向、列方向に処理して統計量を計算し、散布図を作成する。
  - CSV読み込み。`.read_csv`
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-1_Base_DataFrame.png" height="100">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">  
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-2_Adjusted_DataFrame.png"  height="100">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-3_Rate_DataFrame.png"  height="100">

  - DataFrameの行ごとにデータ処理。
      - 1行ずつ評価し、データ抽出。`for idx, df_select in df_original():`
      - 一括で評価し、indexと列名を頼りに、元のデータで上書きする。`df_new = df_new.update(df_original)`
  - DataFrameの列ごとにデータ処理。` df.sum(axis=1)`
  - 列ごとに統計量計算。
  - 平均と分散を使って散布図作成。
  
