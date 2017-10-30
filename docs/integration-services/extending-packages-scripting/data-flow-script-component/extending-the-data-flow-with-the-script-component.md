---
title: "スクリプト コンポーネントによるデータ フローの拡張 |Microsoft ドキュメント"
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
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c58a854082fcbd12333be63995e4fcdf2d55aac7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-data-flow-with-the-script-component"></a>スクリプト コンポーネントによるデータ フローの拡張
  スクリプト コンポーネント、データ フローの機能を拡張[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]で記述されたカスタム コードを持つパッケージ[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual C# でコンパイルおよび実行される、パッケージの実行時にします。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に含まれる変換元、変換、変換先を使用するだけでは完全に要求を満たせない場合でも、スクリプト コンポーネントを使用すれば、カスタムのデータ フロー変換元、変換、変換先を容易に開発できます。 コンポーネントに必要な入力および出力を設定すれば、必要なインフラストラクチャ コードが自動生成されるので、カスタム処理を実行するために必要なコードの記述に集中できます。  
  
 スクリプト コンポーネントのやり取りを含むパッケージと、データ フロー内の自動生成されたクラスを介して、 **ComponentWrapper**と**BufferWrapper**プロジェクト インスタンスである項目の<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>と<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>それぞれクラスです。 このクラスは、接続、変数、および型指定されたオブジェクトとして使用できるその他のパッケージ アイテムを作成し、入力および出力を管理します。 また、カスタム アセンブリだけでなく、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 名前空間および [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリを使用して、スクリプト コンポーネントに独自の機能を実装することもできます。  
  
 スクリプト コンポーネントおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム データ フロー コンポーネントを開発するための手順を大幅に簡略化できます。 ただし、スクリプト コンポーネントのしくみを理解する有用なこと、セクションを読む[カスタム データ フロー コンポーネントを開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)カスタム データ フロー コンポーネントの開発に必要な手順について説明します。  
  
 作成した変換元、変換、変換先を複数のパッケージで再利用する予定がある場合、スクリプト コンポーネントを使用する代わりに、カスタム コンポーネントの開発を検討してください。 詳細については、「 [カスタム データ フロー コンポーネントの開発](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、スクリプト コンポーネントの詳細について説明します。  
  
 [スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成します。](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 プロパティで構成した、**スクリプト変換エディター**機能とスクリプト コンポーネントのコードのパフォーマンスに影響します。  
  
 [コーディングおよびスクリプト コンポーネントのデバッグ](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 使用する、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]スクリプト コンポーネントに含まれているスクリプトを作成する Tools for Applications (VSTA) 開発環境です。  
  
 [スクリプト コンポーネント オブジェクト モデルをについてください。](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 新しいスクリプト コンポーネント プロジェクトには、複数のクラスと自動生成されたプロパティおよびメソッドを含む 3 つのプロジェクト アイテムが含まれています。  
  
 [スクリプト コンポーネントで変数の使用](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 **ComponentWrapper**プロジェクト項目には、パッケージの変数に対して厳密に型指定されたアクセサー プロパティが含まれています。  
  
 [スクリプト コンポーネントでデータ ソースに接続します。](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 **ComponentWrapper**プロジェクト項目には、パッケージで定義された接続に対して厳密に型指定されたアクセサー プロパティも含まれています。  
  
 [スクリプト コンポーネントでイベントを発生させる](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 イベントを発生させて、問題とエラーを通知することができます。  
  
 [スクリプト コンポーネントでログ記録](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 パッケージで有効なログ プロバイダーに情報を記録できます。  
  
 [特定の種類のスクリプト コンポーネントの開発](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 スクリプト コンポーネントを使用してデータ フローの変換元、変換、変換先を開発する方法を、簡単な例を使って説明します。  
  
 [その他のスクリプト コンポーネントの例](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 スクリプト コンポーネントのいくつかの使用方法を、簡単な例を使って説明します。  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネント](../../../integration-services/data-flow/transformations/script-component.md)   
 [スクリプト タスクおよびスクリプト コンポーネントの比較](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  

