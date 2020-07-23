---
title: プログラムによるパッケージとフォルダーの管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c45f6a5b59a65046a0e48fd930fd27d689c0a0a
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913312"
---
# <a name="managing-packages-and-folders-programmatically"></a>プログラムによるパッケージとフォルダーの管理

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


<a name="top"></a> プログラムで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを操作する際に、個々のパッケージやフォルダーが存在するかどうかを判断したり、パッケージが格納されたフォルダーを管理したりする必要がある場合があります。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスは、これらの要件を満たすさまざまなメソッドを提供します。    
    
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> パッケージまたはフォルダーが存在するかどうかの判断    
 保存済みのパッケージの読み込みと実行を行う前に、プログラムによってそのパッケージが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 フォルダーに保存されているパッケージを一覧表示する前に、プログラムによってそのフォルダーが存在するかどうかを判断するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [先頭に戻る](#top)    
    
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> パッケージとフォルダーの管理    
 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 名前空間の <xref:Microsoft.SqlServer.Dts.Runtime> クラスには、パッケージおよびそれを格納するフォルダーの管理用に、追加のメソッドが提供されています。    
    
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> パッケージの削除    
 プログラムにより保存済みパッケージを削除するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [先頭に戻る](#top)    
    
###  <a name="creating-a-folder"></a><a name="managing_create"></a> フォルダーの作成    
 プログラムによりストレージ フォルダーを作成するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [先頭に戻る](#top)    
    
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> フォルダーの削除    
 プログラムによりストレージ フォルダーを削除するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [先頭に戻る](#top)    
    
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> フォルダーの名前変更    
 プログラムによりストレージ フォルダーの名前を変更するには、次のいずれかのメソッドを呼び出します。    
    
|保存先|呼び出すメソッド|    
|----------------------|--------------------|    
|[SSIS パッケージ ストア]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [先頭に戻る](#top)    
    
## <a name="see-also"></a>参照    
 [パッケージの管理 &#40;SSIS サービス&#41;](../../integration-services/service/package-management-ssis-service.md)     
 [プログラムによる使用可能なパッケージの列挙](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
