---
title: "GetPathLocator (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a94f9be78e3acf4d5ea91ec3f538a021890aff16
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="getpathlocator-transact-sql"></a>GetPathLocator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  FileTable 内の指定されたファイルまたはディレクトリのパス ロケーター ID 値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
GetPathLocator(filenamespace_path)  
```  
  
## <a name="arguments"></a>引数  
 *filenamespace_path*  
 FileTable 内の名前空間パス。 型の名前空間のパスは、 **nvarchar (max)**です。  
  
 データベースが Always On 可用性グループに属している場合、 **GetPathLocator**関数は、仮想ネットワーク名 (VNN) またはコンピューター名を受け取ります。  
  
## <a name="return-type"></a>戻り値の型  
 **hierarchyid**  
  
## <a name="general-remarks"></a>全般的な解説  
 詳しくは、「 [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 使用することができます、 **GetPathLocator**ファイル、ファイル サーバーから FileTable に移行するときに機能します。 このシナリオでは、ファイルを FileTable に移動した後、各ファイルの元の UNC パスを FileTable の UNC パスに置き換えます。 完全な例では、次を参照してください。 [Filetable にファイルを読み込む](../../relational-databases/blob/load-files-into-filetables.md)します。  
  
## <a name="see-also"></a>参照  
 [FileTable 内のディレクトリとパスの操作](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
