---
title: "Integration Services 用カスタム オブジェクトの開発 |Microsoft ドキュメント"
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
helpviewer_keywords:
- custom user interface [Integration Services]
- custom objects [Integration Services]
ms.assetid: ca1929a6-0ae6-47d7-b65f-08173b143720
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6bbb7ccd5d65caa4b5c8cc8f28383b8100e09cd6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="developing-custom-objects-for-integration-services"></a>Integration Services 用のカスタム オブジェクトの開発
  ときに、制御フローとデータ フローに含まれているオブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]要件を完全に満たしていない、独自などさまざまな種類のカスタム オブジェクトを開発することができます。  
  
-   **カスタム タスク**です。  
  
-   **カスタム接続マネージャーです。** 現在サポートされていない外部データ ソースに接続します。  
  
-   **カスタム ログ プロバイダーです。** 現在サポートされていない形式でパッケージ イベントを記録します。  
  
-   **カスタム列挙子。** 現在サポートされていないオブジェクトまたは値の形式のセットを反復処理をサポートします。  
  
-   **カスタム データ フロー コンポーネント。** ソース、変換、または変換先として構成できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルにはこのカスタム開発を容易にする複数の基本クラスがあります。これらの基本クラスによって、カスタム実装に対し、一貫した信頼性の高いフレームワークが提供されます。  
  
 カスタム機能を複数のパッケージで再利用する必要がない場合には、スクリプト タスクおよびスクリプト コンポーネントを使用すると、マネージ プログラミング言語を最大限に活用でき、記述するインフラストラクチャ コードが大幅に削減されます。 詳細については、次を参照してください。[スクリプト ソリューションの比較およびカスタム オブジェクト](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)です。  
  
## <a name="steps-in-developing-a-custom-object-for-integration-services"></a>Integration Services 用カスタム オブジェクトの開発手順  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用するカスタム オブジェクトを開発する際には、クラス ライブラリ (DLL) を開発します。このクラス ライブラリは、デザイン時に SSIS デザイナーによって、また実行時に [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムによって、それぞれ読み込まれます。 実装の必要がある最も重要なメソッドは、独自のコードから呼び出すメソッドではなく、ランタイムによって適切な時点で呼び出され、コンポーネントの初期化および検証や、機能の呼び出しを行うメソッドです。  
  
 次に、カスタム オブジェクトの開発手順を示します。  
  
1.  種類がクラス ライブラリの新規プロジェクトを、任意のマネージ プログラミング言語で作成します。  
  
2.  次の表に示す、適切な基本クラスを継承します。  
  
3.  次の表に示す、適切な属性を新しいクラスに適用します。  
  
4.  必要に応じて基本クラスのメソッドをオーバーライドし、オブジェクトのカスタム機能のコードを記述します。  
  
5.  必要に応じて、コンポーネント用のカスタム ユーザー インターフェイスを構築します。 配置を容易にするため、同一ソリューション内の別個のプロジェクトとしてユーザー インターフェイスを開発し、別個のアセンブリとしてビルドすることもできます。  
  
6.  必要に応じてでのサンプルと、カスタム オブジェクトのヘルプ コンテンツへのリンクを表示、 **SSIS ツールボックス**です。  
  
7.  ビルド、配置、および」の説明に従って、新しいカスタム オブジェクトをデバッグ[のビルド、配置、およびカスタム オブジェクトのデバッグ](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)です。  
  
## <a name="base-classes-attributes-and-important-methods"></a>基本クラス、属性、および重要なメソッド  
 この表では、開発可能な各種カスタム オブジェクトに対する、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] オブジェクト モデルの最も重要な要素を簡単に参照できます。  
  
|カスタム オブジェクト|基本クラス|属性|重要なメソッド|  
|-------------------|----------------|---------------|-----------------------|  
|タスク|<xref:Microsoft.SqlServer.Dts.Runtime.Task>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>|  
|[ODBC 入力先エディター]|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>|  
|ログ プロバイダー|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>、 <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>|  
|列挙子|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>|  
|データ フロー コンポーネント|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>|<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>、 <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>|  
  
## <a name="providing-links-to-samples-and-help-content"></a>サンプルとヘルプ コンテンツへのリンクの提供  
 内のリンクを表示する、 **SSIS ツールボックス**サンプルおよびマネージ コードで記述されたカスタム オブジェクトのヘルプ コンテンツの場合に、次のプロパティを使用します。  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpKeyword%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpKeyword%2A>  
  
 ネイティブ コードで記述されたカスタム オブジェクトのサンプルおよびヘルプ コンテンツへのリンクを表示するには、レジストリ スクリプト (.rgs) ファイルに SamplesTag、HelpKeyword、および HelpCollection のエントリを追加します。 例を次に示します。  
  
 `val HelpKeyword = s 'sql11.dts.designer.executepackagetask.F1'`  
  
 `val SamplesTag = s 'ExecutePackageTask'`  
  
## <a name="providing-a-custom-user-interface"></a>カスタム ユーザー インターフェイスの提供  
 カスタム オブジェクトのプロパティをユーザーが構成できるようにするには、カスタム ユーザー インターフェイスの開発も必要になる場合があります。 カスタム ユーザー インターフェイスが特に必要ない場合も、既定のエディターよりもユーザー フレンドリなカスタム ユーザー インターフェイスを作成できます。  
  
 1 つのカスタム ユーザー インターフェイス プロジェクトまたはアセンブリには、通常 2 つのクラスがあります。特定の種類のカスタム オブジェクトのユーザー インターフェイスに対して [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] インターフェイスを実装するクラスと、このクラスによって表示される、ユーザーから情報を収集するための Windows フォームです。 実装するインターフェイスに含まれるメソッドは少数であるため、カスタム ユーザー インターフェイスの開発は難しくありません。  
  
> [!NOTE]  
>  多く[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ログ プロバイダーを実装するカスタム ユーザー インターフェイスがある<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>置き換えて、**構成**テキスト ボックスに使用できる接続マネージャーのフィルター選択されたドロップダウン リスト。 ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、このリリースの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では実装されていません。 そのため、<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> プロパティに値を指定しても、影響がありません。  
  
 次の表では、各種カスタム オブジェクトに対するカスタム ユーザー インターフェイスの開発時に実装が必要なインターフェイスを、簡単に参照できます。 これについても説明します、ユーザーが、オブジェクトに対するカスタム ユーザー インターフェイスを開発しないことを選択した場合、またはオブジェクトを使用して、そのユーザー インターフェイスにリンクに失敗した場合に、 **UITypeName**オブジェクトの属性でプロパティです。 データ フロー コンポーネントにとっては強力な詳細エディターで十分な場合もありますが、タスクや接続マネージャーにとっては [プロパティ] ウィンドウは比較的わかりにくいソリューションであり、カスタム ForEach 列挙子はカスタム フォームなしでは構成不可能です。  
  
|カスタム オブジェクト|ユーザー インターフェイス用の基本クラス|カスタム ユーザー インターフェイスを指定しなかった場合の既定の編集動作|  
|-------------------|-----------------------------------|----------------------------------------------------------------------|  
|タスク|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|[プロパティ] ウィンドウのみ。|  
|[ODBC 入力先エディター]|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>|[プロパティ] ウィンドウのみ。|  
|ログ プロバイダー|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI><br /><br /> ([!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では未実装)|テキスト ボックスに**構成**列|  
|列挙子|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>|プロパティ ウィンドウの場合のみです。 エディターの列挙子構成領域は空です。|  
|データ フロー コンポーネント|<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>|[詳細エディター]|  
  
## <a name="external-resources"></a>外部リソース  
  
-   ブログ エントリ「 [Visual Studio ソリューションのビルド プロセスは、SSIS 参照による .NET Framework アセンブリで間接的な依存関係に関する警告を与える](http://go.microsoft.com/fwlink/?LinkId=215662)、blogs.msdn.com です。  
  
## <a name="see-also"></a>参照  
 [カスタム オブジェクトの永続化](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [カスタム オブジェクトのビルド、配置、デバッグ](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
  
  

