---
title: '[XML ソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmlsourceadapter.connectionmanager.f1
helpviewer_keywords:
- XML Source Editor
ms.assetid: e6507403-a3ce-4b6f-91fc-a7de9f7b6283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ead9ad63b6dfc7d144c0d9e748ad01b847774d85
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419729"
---
# <a name="xml-source-editor-connection-manager-page"></a>[XML ソース エディター] ([接続マネージャー] ページ)
  **[XML ソース エディター]** の **[接続マネージャー]** ページを使用すると、XML ファイルと、XML データを変換する XSD を指定できます。  
  
 XML ソースの詳細については、「 [XML Source](data-flow/xml-source.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **データアクセスモード**  
 ソースからデータを選択する方法を指定します。  
  
|[値]|説明|  
|-----------|-----------------|  
|[XML ファイルの場所]|XML ファイルからデータを取得します。|  
|[変数からの XML ファイル]|XML ファイルの名前を変数で指定します。<br /><br /> **関連情報**: [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)|  
|[変数からの XML データ]|変数から XML データを取得します。|  
  
 **[インライン スキーマを使用する]**  
 XML ソース データ自体に、その構造とデータを定義して検証する XSD スキーマを含めるかどうかを指定します。  
  
 **[XSD の場所]**  
 XSD スキーマ ファイルのパスと名前を入力するか、 **[参照]** をクリックしてファイルを指定します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、XSD スキーマ ファイルを指定します。  
  
 **[XSD の生成]**  
 **[名前を付けて保存]** ダイアログ ボックスを使用して、XSD スキーマ ファイルが自動生成される場所を選択します。 スキーマは XML データの構造から推測されます。  
  
## <a name="data-access-mode-dynamic-options"></a>データ アクセス モードの動的オプション  
  
### <a name="data-access-mode--xml-file-location"></a>[データ アクセス モード] が [XML ファイルの場所] の場合  
 **[XML の場所]**  
 XML データ ファイルのパスと名前を入力するか、 **[参照]** をクリックしてファイルを指定します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、XML データ ファイルを指定します。  
  
### <a name="data-access-mode--xml-file-from-variable"></a>[データ アクセス モード] が [変数からの XML ファイル] の場合  
 **[変数名]**  
 XML ファイルのパスとファイル名を含む変数を選択します。  
  
### <a name="data-access-mode--xml-data-from-variable"></a>[データ アクセス モード] が [変数からの XML データ] の場合  
 **[変数名]**  
 XML データを含む変数を選択します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[XML ソースエディター &#40;列] ページ&#41;](../../2014/integration-services/xml-source-editor-columns-page.md)   
 [XML ソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/xml-source-editor-error-output-page.md)   
 [XML ソースを使用してデータを抽出する](data-flow/extract-data-by-using-the-xml-source.md)  
  
  
