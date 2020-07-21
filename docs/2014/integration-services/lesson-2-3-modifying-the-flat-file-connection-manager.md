---
title: '手順 3: フラット ファイル接続マネージャーの変更 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a3225e4ae703f473e9c7e6679d304da596accba
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440579"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a>手順 3:フラット ファイル接続マネージャーの変更
  この実習では、レッスン 1 で作成、構成したフラット ファイル接続マネージャーを変更します。 フラット ファイル接続マネージャーを作成した当初は、1 つのファイルを静的に読み込むように構成しました。 フラット ファイル接続マネージャーで繰り返しファイルを読み込むには、接続マネージャーの ConnectionString プロパティを修正し、ユーザー定義変数 `User:varFileName`を使用できるようにする必要があります。この変数に、実行時に読み込むファイルのパスを定義します。  
  
 接続マネージャーを修正した後、ユーザー定義変数 `User::varFileName`の値を使用し、接続マネージャーの ConnectionString プロパティを作成します。これにより、接続マネージャーは複数のフラット ファイルに接続できるようになります。 この接続マネージャーを実行すると、Foreach ループ コンテナーの各反復処理により `User::varFileName` 変数が非常に速いスピードで更新されます。 変数が更新されると、接続マネージャーが複数のフラット ファイルに接続され、異なるデータセットを処理するデータ フローのタスクが発生します。  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>接続文字列用の変数を使用するようにフラット ファイル接続マネージャーを構成するには  
  
1.  **接続マネージャー** ペインで、 **[Sample Flat File Source Data]** を右クリックして **[プロパティ]** をクリックします。  
  
2.  プロパティウィンドウの [**式**] で、空のセルをクリックし、省略記号ボタン ([. **..])** をクリックします。  
  
3.  [**プロパティ式エディター** ] ダイアログボックスの [**プロパティ**] 列で、「」と入力するか、を選択し `ConnectionString` ます。  
  
4.  [**式**] 列で、省略記号ボタン **([..** .]) をクリックして [**式ビルダー** ] ダイアログボックスを開きます。  
  
5.  **[式ビルダー]** ダイアログ ボックスで **[変数]** ノードを展開します。  
  
6.  変数**User:: varFileName**を [**式**] ボックスにドラッグします。  
  
7.  **[OK]** をクリックし、 **[式ビルダー]** ダイアログ ボックスを閉じます。  
  
8.  再度 **[OK]** をクリックし、 **[プロパティ式エディター]** ダイアログ ボックスを閉じます。  
  
## <a name="next-lesson-task"></a>次のレッスンの作業  
 [手順 4:レッスン 2 のチュートリアル パッケージのテスト](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
