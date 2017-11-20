---
title: "カスタム接続マネージャーを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2c617741134c19c012f487bc00263c2e4b071810
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-connection-manager"></a>カスタム接続マネージャーの作成
  カスタム接続マネージャーを作成するために必要な手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。  
  
-   基本クラスを継承する新しいクラスを作成します。 接続マネージャー用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> です。  
  
-   クラスに、オブジェクトの種類を識別する属性を適用します。 接続マネージャー用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> です。  
  
-   基本クラスのメソッドとプロパティの実装をオーバーライドします。 接続マネージャーでは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッド、および <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドが対象です。  
  
-   必要に応じて、カスタム ユーザー インターフェイスを開発します。 その場合、接続マネージャーでは、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> インターフェイスを実装するクラスが必要です。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。 そのため、これらのサンプルは組み込みのタスクおよびコンポーネントではテストできません。  
  
## <a name="getting-started-with-a-custom-connection-manager"></a>カスタム接続マネージャーの概要  
  
### <a name="creating-projects-and-classes"></a>プロジェクトおよびクラスの作成  
 すべてのマネージ接続マネージャーは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基本クラスから派生するため、カスタム接続マネージャーを作成するには、最初に任意のマネージ プログラミング言語でクラス ライブラリ プロジェクトを作成してから、基本クラスを継承するクラスを作成します。 この派生クラスで、カスタム機能を実装する基本クラスのプロパティとメソッドがオーバーライドされます。  
  
 同じソリューション内に、もう 1 つのクラス ライブラリ プロジェクトをカスタム ユーザー インターフェイス用に作成します。 更新し、接続マネージャーやそのユーザー インターフェイスを個別に再することができるため、デプロイメントの容易さのユーザー インターフェイスの別のアセンブリがお勧めします。  
  
 どちらのプロジェクトも、アセンブリに署名するよう構成します。アセンブリは、厳密な名前のキー ファイルを使用して、ビルド時に生成されます。  
  
### <a name="applying-the-dtsconnection-attribute"></a>DtsConnection 属性の適用  
 作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性を適用して、そのクラスが接続マネージャーとして識別されるようにします。 この属性には、接続マネージャーの名前、説明、および接続の種類など、デザイン時の情報を指定します。 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>と**説明**に対応するプロパティ、**型**と**説明**に表示される列、 **SSIS 接続マネージャーの追加**内のパッケージの接続を構成するときに表示されるダイアログ ボックスで[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]です。  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> プロパティを使用して、接続マネージャーをそのカスタム ユーザー インターフェイスにリンクします。 使用して、このプロパティに必要な公開キー トークンを取得する**sn.exe t**を使用して、ユーザー インターフェイス アセンブリに署名するキー ペア (.snk) ファイルから公開キー トークンを表示します。  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a>カスタム接続マネージャーのビルド、配置、およびデバッグ  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のカスタム接続マネージャーをビルド、配置、およびデバッグする手順は、他の種類のカスタム オブジェクトの手順と同様です。 詳細については、次を参照してください。[構築, Deploying, and Debugging Custom Objects](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)です。    
  
## <a name="see-also"></a>参照  
 [カスタム接続マネージャーのコーディング](../../../integration-services/extending-packages-custom-objects/connection-manager/coding-a-custom-connection-manager.md)   
 [カスタム接続マネージャーのユーザー インターフェイスの開発](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  

