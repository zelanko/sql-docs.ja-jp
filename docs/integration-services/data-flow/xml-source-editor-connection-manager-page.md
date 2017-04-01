---
title: "[XML ソース エディター] ([接続マネージャー] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.xmlsourceadapter.connectionmanager.f1"
helpviewer_keywords: 
  - "XML ソース エディター"
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
caps.latest.revision: 20
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 20
---
# [XML ソース エディター] ([接続マネージャー] ページ)
  **[XML ソース エディター]** の **[接続マネージャー]** ページを使用すると、XML ファイルと、XML データを変換する XSD を指定できます。  
  
 XML ソースの詳細については、「 [XML Source](../../integration-services/data-flow/xml-source.md)」を参照してください。  
  
## 静的オプション  
 **[データ アクセス モード]**  
 ソースからデータを選択する方法を指定します。  
  
|値|Description|  
|-----------|-----------------|  
|[XML ファイルの場所]|XML ファイルからデータを取得します。|  
|[変数からの XML ファイル]|XML ファイルの名前を変数で指定します。<br /><br /> **関連情報**: [パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)|  
|[変数からの XML データ]|変数から XML データを取得します。|  
  
 **[インライン スキーマを使用する]**  
 XML ソース データ自体に、その構造とデータを定義して検証する XSD スキーマを含めるかどうかを指定します。  
  
 **[XSD の場所]**  
 XSD スキーマ ファイルのパスと名前を入力するか、**[参照]** をクリックしてファイルを指定します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、XSD スキーマ ファイルを指定します。  
  
 **[XSD の生成]**  
 **[名前を付けて保存]** ダイアログ ボックスを使用して、XSD スキーマ ファイルが自動生成される場所を選択します。 スキーマは XML データの構造から推測されます。  
  
## データ アクセス モードの動的オプション  
  
### [データ アクセス モード] が [XML ファイルの場所] の場合  
 **[XML の場所]**  
 XML データ ファイルのパスと名前を入力するか、**[参照]** をクリックしてファイルを指定します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、XML データ ファイルを指定します。  
  
### [データ アクセス モード] が [変数からの XML ファイル] の場合  
 **[変数名]**  
 XML ファイルのパスとファイル名を含む変数を選択します。  
  
### [データ アクセス モード] が [変数からの XML データ] の場合  
 **[変数名]**  
 XML データを含む変数を選択します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[XML ソース エディター] &#40;[列] ページ&#41;](../Topic/XML%20Source%20Editor%20\(Columns%20Page\).md)   
 [XML ソース エディター &#40;[エラー出力] ページ&#41;](../Topic/XML%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [XML ソースを使用してデータを抽出する](../../integration-services/data-flow/extract-data-by-using-the-xml-source.md)  
  
  