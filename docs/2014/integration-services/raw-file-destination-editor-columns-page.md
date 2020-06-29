---
title: '[Raw ファイル変換先エディター] ([列] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a0ceb00767715c3f0b5d149ecd7c8ac3116cf78
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423209"
---
# <a name="raw-file-destination-editor-columns-page"></a>[Raw ファイル変換先エディター] ([列] ページ)
  ファイルに RAW データを書き込むための RAW ファイル変換先を構成するには、RAW ファイル変換先エディターを使用します。  
  
 **どうしたいんですか。**  
  
-   [Raw ファイル変換先エディターを開く](#open)  
  
-   [[接続マネージャー] タブのオプションの設定](#connection)  
  
-   [[列] タブのオプションの設定](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> RAW ファイル変換先エディターを開く  
  
1.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに RAW ファイル変換先を追加します。  
  
2.  コンポーネントを右クリックし、 **[編集]** をクリックします。  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> [接続マネージャー] タブのオプションの設定  
 **アクセスモード**  
 ファイル名の指定方法を選択します。 ファイル名とパスを直接入力するには **[ファイル名]** を選択します。ファイル名を含んでいる変数を指定するには、 **[変数からのファイル名]** を選択します。  
  
 **[ファイル名]** または **[変数名]**  
 RAW ファイルの名前とパスを入力するか、またはファイル名を含んでいる変数を選択します。  
  
 **[書き込みオプション]**  
 ファイルの作成およびファイルへの書き込みに使用するメソッドを選択します。  
  
 **[初期 RAW ファイルの生成]**  
 パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成するには、このボタンをクリックします。 RAW ファイル ソースの参照先を、メタデータのみのファイルにすることができます。  
  
 このボタンをクリックすると、列の一覧が表示されます。 [キャンセル] をクリックして列を変更するか、[OK] をクリックしてファイルの作成を続行することができます。  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a>[列] タブのオプションの設定  
 **[使用できる入力列]**  
 RAW ファイルに書き込む 1 つ以上の入力列を選択します。  
  
 **入力列**  
 **[使用できる入力列]** から選択した場合、このテーブルに入力列が自動的に追加されます。入力列をこのテーブルで直接選択することもできます。  
  
 **出力のエイリアス**  
 出力列に使用する代替名を指定します。  
  
## <a name="see-also"></a>関連項目  
 [RAW ファイル変換先](data-flow/raw-file-destination.md)  
  
  
