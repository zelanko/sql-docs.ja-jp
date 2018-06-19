---
title: '手順 3: フラット ファイル接続マネージャーの変更 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 49aab641ac10aa3f92b59284058b363f3ceba856
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35402924"
---
# <a name="lesson-2-3---modifying-the-flat-file-connection-manager"></a>レッスン 2-3 - フラット ファイル接続マネージャーの変更
この実習では、レッスン 1 で作成、構成したフラット ファイル接続マネージャーを変更します。 フラット ファイル接続マネージャーを作成した当初は、1 つのファイルを静的に読み込むように構成しました。 フラット ファイル接続マネージャーで繰り返しファイルを読み込むには、接続マネージャーの ConnectionString プロパティを修正し、ユーザー定義変数 `User:varFileName`を使用できるようにする必要があります。この変数に、実行時に読み込むファイルのパスを定義します。  
  
接続マネージャーを修正した後、ユーザー定義変数 `User::varFileName`の値を使用し、接続マネージャーの ConnectionString プロパティを作成します。これにより、接続マネージャーは複数のフラット ファイルに接続できるようになります。 この接続マネージャーを実行すると、Foreach ループ コンテナーの各反復処理により `User::varFileName` 変数が非常に速いスピードで更新されます。 変数が更新されると、接続マネージャーが複数のフラット ファイルに接続され、異なるデータセットを処理するデータ フローのタスクが発生します。  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>接続文字列用の変数を使用するようにフラット ファイル接続マネージャーを構成するには  
  
1.  **接続マネージャー** ペインで、 **[Sample Flat File Source Data]** を右クリックして **[プロパティ]** をクリックします。  
  
2.  [プロパティ] ウィンドウの **[Expressions]** で、空のセルをクリックし、参照ボタン ( **[...]**) をクリックします。  
  
3.  **[プロパティ式エディター]** ダイアログ ボックスの **[プロパティ]** 列で「 **ConnectionString**」と入力するか、ConnectionString プロパティを選択します。  
  
4.  **[式]** 列の参照ボタン ( **[...]** ) をクリックし、 **[式ビルダー]** ダイアログ ボックスを開きます。  
  
5.  **[式ビルダー]** ダイアログ ボックスで **[変数]** ノードを展開します。  
  
6.  **User::varFileName**変数を **[式]** ボックスにドラッグします。  
  
7.  **[OK]** をクリックし、 **[式ビルダー]** ダイアログ ボックスを閉じます。  
  
8.  再度 **[OK]** をクリックし、 **[プロパティ式エディター]** ダイアログ ボックスを閉じます。  
  
## <a name="next-lesson-task"></a>次のレッスンの作業  
[手順 4: レッスン 2 のチュートリアル パッケージのテスト](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
  
