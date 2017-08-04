---
title: "パッケージをプログラムによって構築 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: b80495b726ac6fdac713ba028629633bf84cc004
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="building-packages-programmatically"></a>プログラムによるパッケージの構築
  パッケージを動的に作成する必要がある場合、または開発環境以外で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理および実行する必要がある場合は、プログラムでパッケージを操作できます。 この場合、次に示すような一連の方法があります。  
  
-   読み込みおよび変更しなくても、既存のパッケージを実行します。  
  
-   既存のパッケージを読み込み、(別のデータ ソースを指定するなど) 再構成してから実行します。  
  
-   新しいパッケージを作成し、オブジェクト単位やプロパティ単位でコンポーネントを追加および構成し、保存してから実行します。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルを使用すると、任意のマネージ プログラミング言語でパッケージを作成、構成、および実行するコードを記述できます。 たとえば、選択したデータ ソースとそのテーブルおよび列に基づいて、パッケージの接続またはデータ ソース、変換、および変換先を構成するメタデータ ドリブン パッケージの作成が必要になる場合があります。  
  
 ここでは、プログラムを使用してパッケージを行単位で作成および構成する方法を説明し、その例を示します。 パッケージのオプションのプログラミングの範囲のそれほど複雑最後では、単にロードして実行する変更しなくても、既存のパッケージ」の説明に従って[実行し、プログラムによるパッケージの管理](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)です。  
  
 ここに示されていない中レベルの方法としては、既存のパッケージをテンプレートとして読み込み、再構成 (異なるデータ ソースの指定など) してから実行する方法があります。 ここに記載された情報を使用して、パッケージ内の既存のオブジェクトを変更することもできます。  
  
> [!NOTE]  
>  既存のパッケージをテンプレートとして使用し、データ フロー内の既存の列を変更する場合、状況によっては、既存の列を削除してから、影響を受けるコンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドを呼び出す必要があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [プログラムによるパッケージの作成](../../integration-services/building-packages-programmatically/creating-a-package-programmatically.md)  
 プログラムを使用してパッケージを作成する方法について説明します。  
  
 [プログラムによるタスクの追加](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md)  
 タスクをパッケージに追加する方法について説明します。  
  
 [プログラムによるタスクの接続](../../integration-services/building-packages-programmatically/connecting-tasks-programmatically.md)  
 パッケージ内のコンテナーおよびタスクの実行を、前に実行したタスクまたはコンテナーの結果に基づいて制御する方法について説明します。  
  
 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)  
 接続マネージャーをパッケージに追加する方法について説明します。  
  
 [プログラムによる変数の使用](../../integration-services/building-packages-programmatically/working-with-variables-programmatically.md)  
 パッケージの実行中に、変数を追加および使用する方法について説明します。  
  
 [プログラムによるイベントの処理](../../integration-services/building-packages-programmatically/handling-events-programmatically.md)  
 パッケージおよびタスク イベントを処理する方法について説明します。  
  
 [プログラムによるログ記録を有効にします。](../../integration-services/building-packages-programmatically/enabling-logging-programmatically.md)  
 パッケージまたはタスクのログ記録を有効にし、カスタム フィルターをログ イベントに適用する方法について説明します。  
  
 [プログラムによるデータ フロー タスクの追加](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)  
 データ フロー タスクおよびそのコンポーネントを追加して構成する方法について説明します。  
  
 [データ フロー コンポーネントをプログラムで検出します。](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md)  
 ローカル コンピューターにインストールされているコンポーネントの検出方法について説明します。  
  
 [プログラムによるデータ フロー コンポーネントの追加](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
 コンポーネントをデータ フロー タスクに追加する方法について説明します。  
  
 [プログラムによるデータ フロー コンポーネントの接続](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
 2 つのデータ フロー コンポーネントの接続方法について説明します。  
  
 [入力列をプログラムで選択します。](../../integration-services/building-packages-programmatically/selecting-input-columns-programmatically.md)  
 データ フローの上流コンポーネントによってコンポーネントに提供される入力列から、使用する入力列を選択する方法について説明します。  
  
 [プログラムによるパッケージの保存](../../integration-services/building-packages-programmatically/saving-a-package-programmatically.md)  
 プログラムを使用してパッケージを保存する方法について説明します。  
  
## <a name="reference"></a>リファレンス  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)  
 事前に定義されている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [スクリプトによるパッケージの拡張](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 スクリプト タスクを使用した制御フローの拡張方法と、スクリプト コンポーネントを使用したデータ フローの拡張方法について説明します。  
  
 [カスタム オブジェクトを使用したパッケージの拡張](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 複数のパッケージにプログラム カスタム タスク、データ フロー コンポーネント、および使用するためには、その他のパッケージ オブジェクトを作成する方法について説明します。  
  
 [実行していると、プログラムによるパッケージの管理](../../integration-services/run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 パッケージおよびパッケージが保存されているフォルダーを列挙、実行、管理する方法について説明します。  
  
## <a name="external-resources"></a>外部リソース  
  
-   CodePlex サンプル「 [Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkID=131204)、www.codeplex.com/MSFTISProdSamples 上  
  
-   ブログ エントリ「[パフォーマンス カスタム拡張機能をプロファイリング](http://go.microsoft.com/fwlink/?LinkId=238831)、blogs.msdn.com です。  

## <a name="see-also"></a>参照  
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
