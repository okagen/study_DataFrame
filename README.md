# study_DataFrame
---
## study01.
### Extract some element set by using a value in some fields in the DataFrame, and generate a new DataFrame from the element set by swapping the rows and columns.
DataFrame内のあるフィールドに設定された要素の種類ごとにレコードを抽出し、行と列を入れ替えて新しいDataFrameを生成する。
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
## Process the DataFrame in the row and column directions,  then calculate the statistics,  and create a scatter plot.
DataFrame内を行方向、列方向に処理して統計量を計算し、散布図を作成する。
  - CSV読み込み。`.read_csv`
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-1_Base_DataFrame.png" height="150">
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">  
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-2_Adjusted_DataFrame.png"  height="150">


  - DataFrameの行ごとにデータ処理。
      - 1行ずつ評価し、データ抽出。`for idx, df_select in df_original():`
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-3_Rate_DataFrame.png"  height="150">      
            
      - 一括で評価し、indexと列名を頼りに、元のデータで上書きする。`df_new = df_new.update(df_original)`
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-4_Extract_DataFrame.png"  height="150">
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
      
      <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-5_Update_DataFrame.png"  height="150">
      
  - DataFrameの列ごとにデータ処理。` df.sum(axis=1)`
  - 列ごとに統計量計算。
  - 平均と分散を使って散布図作成。
  
  <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/02-6_Scatter_plot.png"  height="200">
  
---
## study03. 
### 3-1. Load some CSV files, and execute some necessary calculations, and generate a new CSV file.
複数のcsvファイルを読み込み、必要な計算をして新しいcsvファイルを生成する。
  - DataFrameの中身を調整。`df.drop()` `df.replace()` `df.astype()` `df.groupby()` `df.rename()` ` df.reset_index`
  - DataFrameを連結する。`pd.concat([dfA, dfB], sort=False)`

    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-0_csv_data.png"  height="150">
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-1_DataFrame.png"  height="150">  
    
### 3-2. Group data in DataFreme by year to draw a bar chart, a scatterplot matrice, and a correlation coefficient.
年毎にグループ化し、棒グラフ、散布図行列、相関係数を求める。

- グループ化して、棒グラフを生成。 `.plot(kind='bar'・・・)`

    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-2-1_groupBy.png"  height="150">
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/00_arrow.png">
  
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-2-2_barChart.png"  height="150">  

  - 散布図行列、相関係数。 `seaborn.pairplot()` `seaborn.heatmap()`
    
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-2-3_seaborn_pairplot.png"  height="150">
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-2-4_correlation.png"  height="150">
  
### 3-3. Specify the level in MultiIndex DataFrame and acquire a subset of the DataFrame, then iterated to create some graphs.
MultiIndex DataFrameのlevelを指定して部分的にDataFrameを取得しイテレーション処理を行ってグラフ化。

  - csvファイルをDataFrameに読みこむ。
  - groupbyでMultiIndex DataFrameを作り処理をする。その際、他のフィールドは平均値としておく。`df.groupby(['Year','Region']).mean()`

    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-3-1_multi_index.png" height="200">
    
  - levelを指定してイテレーションし処理をする。`for idx, df_select in df.groupby(level=[0]):`
  - matplotlib.pyplotを用いてグラフ化。`.plot(kind='line'・・・)`

    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-3-2_line_chart_wo_data_adjustment.png" height="200">
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp
    <img src="https://github.com/okagen/study_DataFrame/blob/master/Data/03-3-3-3_line_chart_w_data_adjustment.png" height="200">
