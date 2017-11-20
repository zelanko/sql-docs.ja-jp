---
title: "カスタム ログ プロバイダーを作成する |Microsoft ドキュメント"
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
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
caps.latest.revision: 58
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4e98f1b5a032353c27ffa1438eb7d01bd517892a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-log-provider"></a>カスタム ログ プロバイダーの作成
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム環境には広範なログ記録機能があります。 ログを使用すると、パッケージの実行中に発生するイベントをキャプチャできます。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、さまざまなログ プロバイダーを使用でき、ログを作成して XML、テキスト、データベースなどの形式で保存したり、Windows イベント ログに格納したりできます。 これらのログ プロバイダーまたは出力形式の中に要件を満たすものがない場合は、カスタム ログ プロバイダーを作成できます。  
  
 カスタム ログ プロバイダーの作成手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。  
  
-   基本クラスを継承する新しいクラスを作成します。 ログ プロバイダー用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> です。  
  
-   クラスに、オブジェクトの種類を識別する属性を適用します。 ログ プロバイダー用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> です。  
  
-   基本クラスのメソッドとプロパティの実装をオーバーライドします。 ログ プロバイダーでは、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッド、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドが対象です。  
  
-   カスタム ログ プロバイダーのカスタム ユーザー インターフェイスが実装されていない[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]です。  
  
## <a name="getting-started-with-a-custom-log-provider"></a>カスタム ログ プロバイダーの概要  
  
### <a name="creating-projects-and-classes"></a>プロジェクトおよびクラスの作成  
 すべてのマネージ ログ プロバイダーは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスから派生するため、カスタム ログ プロバイダーを作成するには、最初に任意のマネージ プログラミング言語でクラス ライブラリ プロジェクトを作成し、基本クラスを継承するクラスを作成します。 この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。  
  
 プロジェクトを構成し、生成するアセンブリを厳密な名前のキー ファイルで署名します。  
  
> [!NOTE]  
>  多く[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]ログ プロバイダーを実装するカスタム ユーザー インターフェイスがある<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>置き換えて、**構成**テキスト ボックスに、 **SSIS ログの構成**フィルター選択されたドロップダウン リストで使用できる接続マネージャー ダイアログ ボックス。 ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。  
  
### <a name="applying-the-dtslogprovider-attribute"></a>DtsLogProvider 属性の適用  
 作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用して、そのクラスがログ プロバイダーとして識別されるようにします。 この属性には、ログ プロバイダーの名前や説明など、デザイン時の情報を指定します。 **DisplayName**と**説明**に対応する属性のプロパティ、**名前**と**説明**に表示される列、 **SSIS ログの構成**エディターで、パッケージ内のログ記録を構成するときに表示される[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]です。  
  
> [!IMPORTANT]  
>  この属性の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> プロパティは使用されません。 ただし、このプロパティには値を入力する必要があります。そうしないと、使用可能なログ プロバイダーの一覧にカスタム ログ プロバイダーが表示されません。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは実装されていません。そのため、<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> プロパティに値を指定しても、影響がありません。  
  
```vb  
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _  
Public Class MyLogProvider  
     Inherits LogProviderBase  
    ' TODO: Override the base class methods.  
End Class  
```  
  
```csharp  
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]  
public class MyLogProvider : LogProviderBase  
{  
    // TODO: Override the base class methods.  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-log-provider"></a>カスタム ログ プロバイダーの作成、配置、およびデバッグ  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でカスタム ログ プロバイダーを作成、配置、およびデバッグする手順は、その他の種類のカスタム オブジェクトで必要な手順とほとんど同様です。 詳細については、次を参照してください。[構築, Deploying, and Debugging Custom Objects](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)です。  
  
## <a name="see-also"></a>参照  
 [カスタム ログ プロバイダーのコーディング](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)   
 [カスタム ログ プロバイダー用ユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-user-interface-for-a-custom-log-provider.md)  
  
  

