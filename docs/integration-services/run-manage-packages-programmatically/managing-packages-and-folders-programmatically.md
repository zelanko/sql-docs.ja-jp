---
title: "プログラムによるパッケージとフォルダーの管理 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: run-manage-packages-programmatically
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
caps.latest.revision: "33"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f53a752a5c6035bef8450a0eeabcbbf27829226d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="managing-packages-and-folders-programmatically"></a>プログラムによるパッケージとフォルダーの管理
<a name="top"></a> プログラムで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、個々のパッケージやフォルダーが存在するかどうかを判断したり、パッケージが格納されたフォルダーを管理したりする必要がある場合があります。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。    
    
##  <a name="exists"></a> パッケージまたはフォルダーが存在するかどうかの判断    
 保存済みのパッケージの読み込みと実行を行う前に、プログラムによってそのパッケージが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 フォルダーに保存されているパッケージを一覧表示する前に、プログラムによってそのフォルダーが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [トップに戻る](#top)    
    
##  <a name="managing"></a> パッケージとフォルダーの管理    
 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスには、パッケージおよびそれを格納するフォルダーの管理用に、追加のメソッドが提供されています。    
    
###  <a name="managing_rempkg"></a> パッケージの削除    
 プログラムにより保存済みパッケージを削除するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [トップに戻る](#top)    
    
###  <a name="managing_create"></a> フォルダーの作成    
 プログラムによりストレージ フォルダーを作成するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [トップに戻る](#top)    
    
###  <a name="managing_remfldr"></a> フォルダーの削除    
 プログラムによりストレージ フォルダーを削除するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [トップに戻る](#top)    
    
###  <a name="managing_rename"></a> フォルダーの名前変更    
 プログラムによりストレージ フォルダーの名前を変更するには、次のいずれかのメソッドを呼び出します。    
    
|ストレージの場所|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [トップに戻る](#top)    
    
## <a name="see-also"></a>参照    
 [パッケージの管理 &#40;SSIS サービス&#41;](../../integration-services/service/package-management-ssis-service.md)     
 [プログラムによる使用可能なパッケージの列挙](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
