---
title: "カスタム データ フロー コンポーネントの開発 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f25c74b52eaccb6c7b0e92cb7dace3d56f3cdd83
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-data-flow-component"></a>カスタム データ フロー コンポーネントの開発
  データ フロー タスクは、さまざまなデータ ソースに接続し、そのデータを高速で変換およびルーティングするコンポーネントで構成されています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]により、開発者はカスタム変換元、変換、およびで使用できる変換先を作成する拡張可能なオブジェクト モデルを提供[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でパッケージを展開します。 ここでは、カスタム データ フロー コンポーネントの開発に役立つトピックを紹介します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [カスタム データ フロー コンポーネントの作成](../../../integration-services/extending-packages-custom-objects/data-flow/creating-a-custom-data-flow-component.md)  
 カスタム データ フロー コンポーネントを作成するための初期手順について説明します。  
  
 [データ フロー コンポーネントのデザイン時のメソッド](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md)  
 カスタム データ フロー コンポーネントに実装する、デザイン時のメソッドについて説明します。  
  
 [データ フロー コンポーネントの実行時のメソッド](../../../integration-services/extending-packages-custom-objects/data-flow/run-time-methods-of-a-data-flow-component.md)  
 カスタム データ フロー コンポーネントに実装する、実行時のメソッドについて説明します。  
  
 [実行プランおよびバッファーの割り当て](../../../integration-services/extending-packages-custom-objects/data-flow/execution-plan-and-buffer-allocation.md)  
 データ フローの実行プラン、およびデータ バッファーの割り当てについて説明します。  
  
 [データ フロー内のデータ型の使用](../../../integration-services/extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)  
 データ フローが [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] データ型をどのように .NET Framework マネージ データ型にマップするかについて説明します。  
  
 [データ フロー コンポーネントの検証](../../../integration-services/extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)  
 コンポーネントの構成の検証、およびコンポーネントのメタデータの再構成に使用するメソッドについて説明します。  
  
 [外部メタデータの実装](../../../integration-services/extending-packages-custom-objects/data-flow/implementing-external-metadata.md)  
 データ検証用の外部メタデータ列の使用方法について説明します。  
  
 [発生して、イベントを定義するデータ フロー コンポーネント](../../../integration-services/extending-packages-custom-objects/data-flow/raising-and-defining-events-in-a-data-flow-component.md)  
 定義済みのイベントおよびカスタム イベントの起動方法について説明します。  
  
 [ログ記録とログ エントリを定義するデータ フロー コンポーネント](../../../integration-services/extending-packages-custom-objects/data-flow/logging-and-defining-log-entries-in-a-data-flow-component.md)  
 カスタム ログ エントリの作成方法およびカスタム ログ エントリへの書き込み方法について説明します。  
  
 [データ フロー コンポーネントでエラー出力の使用](../../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)  
 エラー行を別の出力にリダイレクトする方法について説明します。  
  
 [データ フロー コンポーネントのバージョンのアップグレード](../../../integration-services/extending-packages-custom-objects/data-flow/upgrading-the-version-of-a-data-flow-component.md)  
 新しいバージョンのコンポーネントが最初に使用されるときに、保存されたコンポーネント メタデータを更新する方法について説明します。  
  
 [データ フロー コンポーネント用ユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-user-interface-for-a-data-flow-component.md)  
 コンポーネント用のカスタム エディターの実装方法について説明します。  
  
 [開発の特定種類のデータ フロー コンポーネント](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
 変換元、変換、および変換先の、3 種類のデータ フロー コンポーネントの開発に関する情報が含まれています。  
  
## <a name="reference"></a>リファレンス  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 カスタム データ フロー コンポーネントを作成するために使用するクラスやインターフェイスが含まれています。  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 データ フロー タスクのオブジェクト モデルを構成するクラスおよびインターフェイスが含まれており、これを使用するとカスタム データ フロー コンポーネントを作成したり、データ フロー タスクを構築できます。  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>  
 データ フロー コンポーネント用のユーザー インターフェイスの作成に使用する、クラスおよびインターフェイスが含まれています。  
  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)  
 事前に定義されている [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] エラー コードと、そのシンボル名および説明の一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
  
### <a name="information-common-to-all-custom-objects"></a>すべてのカスタム オブジェクトに共通の情報  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] で作成可能なカスタム オブジェクトのすべての種類に共通の情報については、次のトピックを参照してください。  
  
 [Integration Services 用のカスタム オブジェクトの開発](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 カスタム オブジェクトのすべての型を実装する基本的な手順について説明します[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]です。  
  
 [カスタム オブジェクトの永続化](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 カスタムの永続性と、それが必要な場合について説明します。  
  
 [カスタム オブジェクトのビルド、配置、デバッグ](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 カスタム オブジェクトをビルド、署名、配置、およびデバッグする方法について説明します。  
  
### <a name="information-about-other-custom-objects"></a>その他のカスタム オブジェクトに関する情報  
 作成できるカスタム オブジェクトの他の種類について[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]、次のトピックを参照してください。  
  
 [カスタム タスクの開発](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 カスタム タスクのプログラム方法について説明します。  
  
 [カスタム接続マネージャーの開発](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 カスタム接続マネージャーのプログラム方法について説明します。  
  
 [カスタム ログ プロバイダーの開発](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 カスタム ログ プロバイダーのプログラム方法について説明します。  
  
 [カスタム ForEach 列挙子の開発](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 カスタム列挙子のプログラム方法について説明します。  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネントによるデータ フローの拡張](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
 [スクリプティング ソリューションとカスタム オブジェクトの比較](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  

