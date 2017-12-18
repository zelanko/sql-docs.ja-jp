---
title: "パッケージをプログラムで保存 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6a433d64b0c2b7694dfe1fc89db6dc6df9060b54
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="saving-a-package-programmatically"></a>パッケージをプログラムで保存
  プログラムにより新しいパッケージを構築したり、既存のパッケージを変更した後には、通常は変更を保存します。  
  
 このトピックでパッケージを保存するために使うすべてのメソッドには、**Microsoft.SqlServer.ManagedDTS** アセンブリへの参照が必要です。 新しいプロジェクトに参照を追加した後、**using** または **Imports** ステートメントを使って <xref:Microsoft.SqlServer.Dts.Runtime> 名前空間をインポートします。  
  
## <a name="saving-a-package-programmatically"></a>パッケージをプログラムで保存  
 プログラムによりパッケージを保存するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスの次のいずれかのメソッドを呼び出します。  
  
|ストレージの場所|呼び出すメソッド|  
|----------------------|--------------------|  
|ファイル|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> または<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドは、"." またはローカル サーバーのサーバー名のみをサポートします。 "(local)" や "localhost" は使用できません。  
  
## <a name="see-also"></a>参照  
 [パッケージを保存する](../../integration-services/save-packages.md)  
  
  
