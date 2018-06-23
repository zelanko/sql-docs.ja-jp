---
title: プログラムによるパッケージのロールの管理 (SSIS Service) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 31370f62260feeb32724e3bcb304a9c61270c627
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173749"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>プログラムによるパッケージのロールの管理 (SSIS Service)
  プログラムによって [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を操作する際に、どのロールをパッケージに適用できるかどうかを確認したり、個々のパッケージに適用されているロールを確認または設定することが必要な場合があります。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。  
  
 ロールは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** データベースに格納されたパッケージにのみ適用されます。 パッケージ ロールの詳細については、「[Integration Services のロール &#40;SSIS サービス&#41;](../security/integration-services-roles-ssis-service.md)」を参照してください。  
  
 このトピックで説明するすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。 新しいプロジェクトで、参照を追加すると、インポート、<xref:Microsoft.SqlServer.Dts.Runtime>名前空間を使用して、`using`または`Imports`ステートメントです。  
  
> [!IMPORTANT]  
>  SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドでは、"."、localhost、またはローカル サーバーのサーバー名のみがサポートされます。 "(local)" は使用できません。  
  
## <a name="determining-which-roles-are-available"></a>使用できるロールの確認  
 特定のサーバーに格納されているパッケージで使用できるロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> クラスの <xref:Microsoft.SqlServer.Dts.Runtime.Application> メソッドを呼び出します。  
  
## <a name="determining-which-roles-are-assigned"></a>割り当てられたロールの確認  
 特定のパッケージに既に割り当てられているロールを確認するには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> メソッドを呼び出します。 パッケージにロールを割り当てるには、<xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> メソッドを呼び出します。  
  
![Integration Services のアイコン (小)](../media/dts-16.gif "Integration Services アイコン (小)")**Integration Services と終了日を維持** <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照してください。](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のロール (SSIS サービス)](../security/integration-services-roles-ssis-service.md)  
  
  