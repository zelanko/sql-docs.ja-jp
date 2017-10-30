---
title: "ロールをプログラムによるパッケージの管理 (SSIS サービス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 7a7fb000389756caf0c2f2ea00cd0b80e75557d8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="managing-package-roles-programmatically-ssis-service"></a>プログラムによるパッケージのロールの管理 (SSIS Service)
  プログラムによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を操作する際に、どのロールをパッケージに適用できるかどうかを確認したり、個々のパッケージに適用されているロールを確認または設定することが必要な場合があります。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。  
  
 ロールに格納されたパッケージにのみ適用、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**データベース。 パッケージのロールの詳細については、次を参照してください。 [Integration Services のロール & #40 です。SSIS サービス &#41;](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
 このトピックで説明したすべてのメソッドへの参照が必要、 **Microsoft.SqlServer.ManagedDTS**アセンブリ。 新しいプロジェクトで参照を追加した後でインポート、<xref:Microsoft.SqlServer.Dts.Runtime>名前空間を使用して、**を使用して**または**Imports**ステートメントです。  
  
> [!IMPORTANT]  
>  メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.Application>だけをサポートして SSIS パッケージ ストアを作業用のクラス"です。"、localhost、またはサーバーがローカル サーバーの名前。 "(local)" は使用できません。  
  
## <a name="determining-which-roles-are-available"></a>使用できるロールの確認  
 特定のサーバーに格納されているパッケージで使用できるロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> クラスの <xref:Microsoft.SqlServer.Dts.Runtime.Application> メソッドを呼び出します。  
  
## <a name="determining-which-roles-are-assigned"></a>割り当てられたロールの確認  
 特定のパッケージに既に割り当てられているロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> メソッドを呼び出します。 パッケージにロールを割り当てるには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> メソッドを呼び出します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のロール & #40 です。SSIS サービス &#41;](../../integration-services/security/integration-services-roles-ssis-service.md)  
  
  

