---
title: "パッケージをプログラムで保存 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: building-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: f6b99377f6eaf720b9511b560e5cf563ede2b869
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="saving-a-package-programmatically"></a>プログラムによるパッケージの保存
  プログラムにより新しいパッケージを構築したり、既存のパッケージを変更した後には、通常は変更を保存します。  
  
 参照を必要なすべてのパッケージを保存する、このトピックで使用される方法、 **Microsoft.SqlServer.ManagedDTS**アセンブリ。 新しいプロジェクトで、参照を追加すると、インポート、<xref:Microsoft.SqlServer.Dts.Runtime>を持つ名前空間、**を使用して**または**Imports**ステートメント。  
  
## <a name="saving-a-package-programmatically"></a>プログラムによるパッケージの保存  
 パッケージをプログラムで保存するには、次のメソッドのいずれかを呼び出して、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application>クラス。  
  
|ストレージの場所|呼び出すメソッド|  
|----------------------|--------------------|  
|ファイル|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> または<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドは、"." またはローカル サーバーのサーバー名のみをサポートします。 "(local)" や "localhost" は使用できません。  
  
## <a name="see-also"></a>参照  
 [パッケージを保存する](../../integration-services/save-packages.md)  
  
  

