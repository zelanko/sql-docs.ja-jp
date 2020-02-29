---
title: カスタム データ フロー コンポーネントの開発 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 061daaa3b44c151a1f77b075bef66ef90570af98
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176352"
---
# <a name="developing-a-custom-data-flow-component"></a>カスタム データ フロー コンポーネントの開発
  データ フロー タスクは、さまざまなデータ ソースに接続し、そのデータを高速で変換およびルーティングするコンポーネントで構成されています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、拡張可能なオブジェクト モデルが用意されており、開発者はそのオブジェクト モデルを使用して、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] や配置されたパッケージで使用できるカスタム変換元、カスタム変換、およびカスタム変換先を作成できます。 ここでは、カスタム データ フロー コンポーネントの開発に役立つトピックを紹介します。

## <a name="in-this-section"></a>このセクションの内容
 [カスタムデータフローコンポーネントの作成](creating-a-custom-data-flow-component.md)カスタムデータフローコンポーネントを作成するための最初の手順について説明します。

 [データフローコンポーネントのデザイン時のメソッド](design-time-methods-of-a-data-flow-component.md)カスタムデータフローコンポーネントに実装するデザイン時のメソッドについて説明します。

 [データフローコンポーネントの実行時のメソッド](run-time-methods-of-a-data-flow-component.md)カスタムデータフローコンポーネントに実装する実行時のメソッドについて説明します。

 [実行プランとバッファー割り当て](execution-plan-and-buffer-allocation.md)データフロー実行プランとデータバッファーの割り当てについて説明します。

 [データフローでのデータ型の操作](working-with-data-types-in-the-data-flow.md)データフローがデータ型を[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] .NET Framework マネージデータ型にマップする方法について説明します。

 [データフローコンポーネントの検証](validating-a-data-flow-component.md)コンポーネントの構成を検証し、コンポーネントのメタデータを再構成するために使用する方法について説明します。

 [外部メタデータの実装](implementing-external-metadata.md)データの検証に外部メタデータ列を使用する方法について説明します。

 [データフローコンポーネントでのイベントの発生と定義](raising-and-defining-events-in-a-data-flow-component.md)定義済みおよびカスタムイベントを発生させる方法について説明します。

 [データフローコンポーネントのログエントリのログ記録と定義](logging-and-defining-log-entries-in-a-data-flow-component.md)カスタムログエントリを作成して書き込む方法について説明します。

 [データフローコンポーネントでのエラー出力の使用](using-error-outputs-in-a-data-flow-component.md)エラー行を別の出力にリダイレクトする方法について説明します。

 [データフローコンポーネントのバージョンのアップグレード](upgrading-the-version-of-a-data-flow-component.md)コンポーネントの新しいバージョンが最初に使用されたときに、保存されたコンポーネントのメタデータを更新する方法について説明します。

 [データフローコンポーネントのユーザーインターフェイスの開発](developing-a-user-interface-for-a-data-flow-component.md)コンポーネントのカスタムエディターを実装する方法について説明します。

 [特定の種類のデータフローコンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)変換元、変換、および変換先という3種類のデータフローコンポーネントの開発について説明します。

## <a name="reference"></a>リファレンス
 <xref:Microsoft.SqlServer.Dts.Pipeline>カスタムデータフローコンポーネントの作成に使用されるクラスとインターフェイスが含まれています。

 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>データフロータスクオブジェクトモデルを構成するクラスとインターフェイスが含まれています。これは、カスタムデータフローコンポーネントを作成したり、データフロータスクを作成したりするために使用されます。

 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>データフローコンポーネントのユーザーインターフェイスを作成するために使用されるクラスとインターフェイスが含まれています。

 [Integration Services のエラーとメッセージの参照](../../integration-services-error-and-message-reference.md)定義済み[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]のエラーコードとそのシンボル名と説明を一覧表示します。

## <a name="related-sections"></a>関連項目

### <a name="information-common-to-all-custom-objects"></a>すべてのカスタム オブジェクトに共通の情報
 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。

 [Integration Services 用のカスタムオブジェクトの開発](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)のすべての種類のカスタムオブジェクトを実装するため[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]の基本的な手順について説明します。

 [カスタムオブジェクトの永続](../../extending-packages-custom-objects/persisting-custom-objects.md)化カスタムの永続性について説明し、必要な場合について説明します。

 [カスタムオブジェクトのビルド、配置、およびデバッグ](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)カスタムオブジェクトのビルド、署名、配置、およびデバッグの手法について説明します。

### <a name="information-about-other-custom-objects"></a>その他のカスタム オブジェクトに関する情報
 
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なその他の種類のカスタム オブジェクトについては、次のトピックを参照してください。

 [カスタムタスクの開発](../../extending-packages-custom-objects/task/developing-a-custom-task.md)カスタムタスクをプログラミングする方法について説明します。

 [カスタム接続マネージャーの開発](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)カスタム接続マネージャーをプログラミングする方法について説明します。

 [カスタムログプロバイダーの開発](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)カスタムログプロバイダーをプログラミングする方法について説明します。

 [カスタム ForEach 列挙子の開発](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)カスタム列挙子をプログラミングする方法について説明します。

![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services に関するページを参照してください。](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>参照
 [スクリプトコンポーネントによるデータフローの拡張](../../extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md[スクリプトソリューションとカスタムオブジェクトの比較](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)


