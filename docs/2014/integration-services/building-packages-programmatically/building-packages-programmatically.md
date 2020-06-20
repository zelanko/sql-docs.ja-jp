---
title: プログラムによるパッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 7474b1f4-7607-4f28-a6fd-67f7db1dd3f8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3d69416b36969e564b611d1b1274367b6ce5cb86
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84924973"
---
# <a name="building-packages-programmatically"></a>プログラムによるパッケージの作成
  パッケージを動的に作成する必要がある場合、または開発環境以外で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを管理および実行する必要がある場合は、プログラムでパッケージを操作できます。 この場合、次に示すような一連の方法があります。

-   既存のパッケージを読み込んで、変更せずに実行します。

-   既存のパッケージを読み込み、(別のデータ ソースを指定するなど) 再構成してから実行します。

-   新しいパッケージを作成し、オブジェクト単位やプロパティ単位でコンポーネントを追加および構成し、保存してから実行します。

 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルを使用すると、任意のマネージド プログラミング言語でパッケージを作成、構成、および実行するコードを記述できます。 たとえば、選択したデータ ソースとそのテーブルおよび列に基づいて、パッケージの接続またはデータ ソース、変換、および変換先を構成するメタデータ ドリブン パッケージの作成が必要になる場合があります。

 ここでは、プログラムを使用してパッケージを行単位で作成および構成する方法を説明し、その例を示します。 パッケージ プログラミングの最も簡単な方法では、「[プログラムによるパッケージの実行と管理](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)」に示すように、既存のパッケージを読み込んで、変更せずに実行できます。

 ここに示されていない中レベルの方法としては、既存のパッケージをテンプレートとして読み込み、再構成 (異なるデータ ソースの指定など) してから実行する方法があります。 ここに記載された情報を使用して、パッケージ内の既存のオブジェクトを変更することもできます。

> [!NOTE]
>  既存のパッケージをテンプレートとして使用し、データ フロー内の既存の列を変更する場合、状況によっては、既存の列を削除してから、影響を受けるコンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> メソッドを呼び出す必要があります。

## <a name="in-this-section"></a>このセクションの内容
 [プログラムによるパッケージの作成](../building-packages-programmatically/creating-a-package-programmatically.md)プログラムによってパッケージを作成する方法について説明します。

 [プログラムによるタスクの追加](../building-packages-programmatically/adding-tasks-programmatically.md)パッケージにタスクを追加する方法について説明します。

 [プログラムによるタスクの接続](../building-packages-programmatically/connecting-tasks-programmatically.md)前のタスクまたはコンテナーの実行結果に基づいて、パッケージ内のコンテナーおよびタスクの実行を制御する方法について説明します。

 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)接続マネージャーをパッケージに追加する方法について説明します。

 [プログラムによる変数の](../building-packages-programmatically/working-with-variables-programmatically.md)使用パッケージの実行中に変数を追加して使用する方法について説明します。

 [プログラムによるイベントの処理](../building-packages-programmatically/handling-events-programmatically.md)パッケージとタスクのイベントを処理する方法について説明します。

 [プログラムによるログ記録の有効化](../building-packages-programmatically/enabling-logging-programmatically.md)パッケージまたはタスクのログ記録を有効にする方法と、カスタムフィルターをログイベントに適用する方法について説明します。

 [プログラムによるデータフロータスクの追加](../building-packages-programmatically/adding-the-data-flow-task-programmatically.md)データフロータスクとそのコンポーネントを追加して構成する方法について説明します。

 [プログラムによるデータフローコンポーネントの検出](../building-packages-programmatically/discovering-data-flow-components-programmatically.md)ローカルコンピューターにインストールされているコンポーネントを検出する方法について説明します。

 [プログラムによるデータフローコンポーネントの追加](../building-packages-programmatically/adding-data-flow-components-programmatically.md)コンポーネントをデータフロータスクに追加する方法について説明します。

 [プログラムによるデータフローコンポーネントの接続](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)2つのデータフローコンポーネントを接続する方法について説明します。

 [プログラムによる入力列の選択](../building-packages-programmatically/selecting-input-columns-programmatically.md)データフローの上流コンポーネントによってコンポーネントに提供される入力列を選択する方法について説明します。

 [プログラムによるパッケージの保存](../building-packages-programmatically/saving-a-package-programmatically.md)プログラムによってパッケージを保存する方法について説明します。

## <a name="reference"></a>リファレンス
 [Integration Services のエラーとメッセージの参照](../integration-services-error-and-message-reference.md)定義済みの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラーコードとそのシンボル名と説明を一覧表示します。

## <a name="related-sections"></a>関連項目
 [スクリプトを使用したパッケージの拡張](../extending-packages-scripting/extending-packages-with-scripting.md)スクリプトタスクを使用して制御フローを拡張する方法と、スクリプトコンポーネントを使用してデータフローを拡張する方法について説明します。

 [カスタムオブジェクトを使用したパッケージの拡張](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)複数のパッケージで使用するプログラムカスタムタスク、データフローコンポーネント、およびその他のパッケージオブジェクトを作成する方法について説明します。

 [プログラムによるパッケージの実行と管理](../run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)パッケージ、およびパッケージが格納されているフォルダーを列挙、実行、および管理する方法について説明します。

## <a name="external-resources"></a>外部リソース

-   [www.codeplex.com/MSFTISProdSamples](www.codeplex.com/MSFTISProdSamples) の CodePlex サンプル「[Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkID=131204)」

-   blogs.msdn.com のブログ「[カスタム拡張機能のパフォーマンスのプロファイル](https://go.microsoft.com/fwlink/?LinkId=238831)」

![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>参照
 [SQL Server Integration Services](../sql-server-integration-services.md)


