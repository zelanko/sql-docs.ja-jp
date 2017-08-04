---
title: "Raw ファイル変換先エディター (接続マネージャー ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9f27180b2dca144905af1a5346d3d8747aa8248a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="raw-file-destination-editor-connection-manager-page"></a>[RAW ファイル変換先エディター] ([接続マネージャー] ページ)
  ファイルに RAW データを書き込むための RAW ファイル変換先を構成するには、RAW ファイル変換先エディターを使用します。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [RAW ファイル変換先エディターを開く](#open)  
  
-   [[接続マネージャー] タブのオプションの設定](#connection)  
  
-   [[列] タブのオプションの設定](#mapping)  
  
##  <a name="open"></a> RAW ファイル変換先エディターを開く  
  
1.  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]パッケージに RAW ファイル変換先を追加します。  
  
2.  コンポーネントを右クリックし、 **[編集]**をクリックします。  
  
##  <a name="connection"></a> [接続マネージャー] タブのオプションの設定  
 **[アクセス モード]**  
 ファイル名の指定方法を選択します。 ファイル名とパスを直接入力するには **[ファイル名]** を選択します。ファイル名を含んでいる変数を指定するには、 **[変数からのファイル名]** を選択します。  
  
 **[ファイル名]** または **[変数名]**  
 RAW ファイルの名前とパスを入力するか、またはファイル名を含んでいる変数を選択します。  
  
 **[書き込みオプション]**  
 ファイルの作成およびファイルへの書き込みに使用するメソッドを選択します。  
  
 **[初期 RAW ファイルの生成]**  
 パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成するには、このボタンをクリックします。 ファイルには、 **[RAW ファイル変換先エディター]** の **[列]**ページで選択した列が含まれています。 RAW ファイル ソースの参照先を、このメタデータのみのファイルにすることができます。  
  
 **[初期 RAW ファイルの生成]**をクリックすると、メッセージ ボックスが表示されます。 ファイルの作成を続行するには、 **[OK]** をクリックします。 **[列]** ページで別の列の一覧を選択するには、 **[キャンセル]** をクリックします。  
  
##  <a name="mapping"></a> [列] タブのオプションの設定  
 **使用できる入力列**  
 RAW ファイルに書き込む 1 つ以上の入力列を選択します。  
  
 **入力列**  
 **[使用できる入力列]**から選択した場合、このテーブルに入力列が自動的に追加されます。入力列をこのテーブルで直接選択することもできます。  
  
 **[出力の別名]**  
 出力列に使用する代替名を指定します。  
  
## <a name="see-also"></a>参照  
 [RAW ファイル変換先](../../integration-services/data-flow/raw-file-destination.md)  
  
  
