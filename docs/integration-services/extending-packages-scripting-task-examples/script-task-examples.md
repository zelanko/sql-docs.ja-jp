---
title: "タスクの例のスクリプトを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f7732abe880aa5eeaab2030da423e18d1977d64a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="script-task-examples"></a>スクリプト タスクの例
  スクリプト タスクは複数の用途を持つツールで、パッケージで使用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に組み込まれているタスクでは満たせないほとんどすべての要件を満たすことができます。 このトピックでは、使用できる機能の一部を示すスクリプト タスクのコード例について説明します。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、これらのスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
### <a name="example-topics"></a>コード例のトピック  
 このセクションに含まれるコード例では、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] スクリプト タスクに組み込むことができる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] クラスのさまざまな使用方法を示します。  
  
 [スクリプト タスクによる空のフラット ファイルの検出](../../integration-services/extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 フラット ファイルをチェックして、データ行が含まれているかどうかを判別し、結果を変数に保存して制御フローの分岐で使用できるようにします。  
  
 [スクリプト タスクによる ForEach ループの一覧の収集](../../integration-services/extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 ユーザー指定条件に適合するファイルのリストを収集し、後に Foreach from Variable 列挙子で使用できるように変数を設定します。  
  
 [スクリプト タスクによる Active Directory へのクエリの実行](../../integration-services/extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 値に基づいて Active Directory からユーザー情報を取得、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] System.DirectoryServices 名前空間のクラスを使用して、変数です。  
  
 [スクリプト タスクによるパフォーマンス カウンターの監視](../../integration-services/extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 実行の進行状況を追跡するために使用できるカスタム パフォーマンス カウンターを作成、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] System.Diagnostics 名前空間のクラスを使用して、パッケージです。  
  
 [スクリプト タスクによる画像の操作](../../integration-services/extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 画像を JPEG 形式に圧縮し、system.drawing の各名前空間のクラスを使用して、そこからサムネイル画像を作成します。  
  
 [スクリプト タスクによるインストールされたプリンターの検索](../../integration-services/extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 System.Drawing.Printing 名前空間のクラスを使用して、特定の用紙サイズをサポートするインストール済みのプリンターを検索します。  
  
 [スクリプト タスクによる HTML メール メッセージの送信](../../integration-services/extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 プレーン テキスト形式の代わりに HTML 形式でメール メッセージを送信します。  
  
 [スクリプト タスクを使用した Excel ファイルの操作](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 Excel ファイル内のワークシートを一覧表示し、特定のワークシートが存在するかどうかチェックします。  
  
 [スクリプト タスクによるリモート プライベート メッセージ キューへの送信](../../integration-services/extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 リモート プライベート メッセージ キューにメッセージを送信します。  
  
### <a name="other-examples"></a>その他の例  
 次のトピックでは、スクリプト タスクで使用するためのコード例も紹介します。  
  
 [スクリプト タスクでの変数の使用](../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 パッケージ変数の値が別の変数で指定した制限を超える可能性がある場合、パッケージの実行を継続するかどうかをユーザーに確認します。  
  
 [スクリプト タスクでのデータ ソースへの接続](../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 パッケージで定義された接続マネージャーから、接続または接続情報を取得します。  
  
 [スクリプト タスクでのイベントの発生](../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 サーバー上のインターネット接続の状態に基づき、エラー、警告、または情報メッセージを返します。  
  
 [スクリプト タスクでのログ記録](../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 タスクによって処理されたアイテム数を、有効なログ プロバイダーに記録します。  
  
  
