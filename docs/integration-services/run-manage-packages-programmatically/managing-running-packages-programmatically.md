---
title: "プログラムによるパッケージの実行を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 34f2c773e89c0162df5d13a16d27f01eb5d8f4df
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="managing-running-packages-programmatically"></a>プログラムによるパッケージの実行の管理
  プログラムによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、現在実行中のパッケージを特定することが必要な場合があります。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすメソッドとクラスを提供します。  
  
 パッケージの監視の詳細については、次を参照してください。[パッケージの管理 & #40 です。SSIS サービス &#41;](../../integration-services/service/package-management-ssis-service.md).  
  
 このトピックで説明したすべてのメソッドへの参照が必要、 **Microsoft.SqlServer.ManagedDTS**アセンブリ。 新しいプロジェクトで、参照を追加すると、インポート、<xref:Microsoft.SqlServer.Dts.Runtime>を持つ名前空間、**を使用して**または**Imports**ステートメント。  
  
> [!IMPORTANT]  
>  メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.Application>だけをサポートして SSIS パッケージ ストアを作業用のクラス"です。"、localhost、またはサーバーがローカル サーバーの名前。 "(local)" は使用できません。  
  
## <a name="determining-which-packages-are-currently-running"></a>現在実行中のパッケージの特定  
 特定のサーバーでどのパッケージが現在実行されているかを調べるには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A> メソッドを呼び出します。 このメソッドは、<xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> コレクションを返します。  
  
> [!NOTE]  
>  管理者に対しては、現在コンピューターで実行されているすべてのパッケージが表示されます。他のユーザーに対しては、自分が起動したパッケージのみが表示されます。  
  
## <a name="working-with-running-packages"></a>実行中のパッケージの操作  
 現在実行中のパッケージを特定した後、そのパッケージの情報を取得したり、パッケージの停止を要求することができます。  
  
### <a name="getting-information-about-a-running-package"></a>実行中のパッケージの情報の取得  
 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> コレクションを反復処理するときに、<xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> オブジェクトのプロパティを使用して、パッケージを探したり、実行中のパッケージに関する追加情報を取得することができます。  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a>実行中のパッケージの停止  
 <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> オブジェクトの <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> メソッドを呼び出して、そのパッケージを停止するように要求できます。 パッケージが実際に停止する時間と停止要求が発行される時間の間に遅延が生じる場合があります。  
  
## <a name="see-also"></a>参照  
 [パッケージの管理 & #40 です。SSIS サービス &#41;](../../integration-services/service/package-management-ssis-service.md)   
 [プログラムで使用可能なパッケージの列挙](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
