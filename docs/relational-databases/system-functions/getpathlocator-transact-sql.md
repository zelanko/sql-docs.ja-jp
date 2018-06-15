---
title: GetPathLocator (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetPathLocator
- GetPathLocator_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetPathLocator function
ms.assetid: 78b7e220-445b-4fdf-811b-7253f4f2b058
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0b7714606336e46d25459d972b0bd0f4f319a529
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225422"
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
 FileTable 内の名前空間パス。 型の名前空間のパスは、 **nvarchar (max)** です。  
  
 データベースが Always On 可用性グループに属している場合、 **GetPathLocator**関数は、仮想ネットワーク名 (VNN) またはコンピューター名を受け取ります。  
  
## <a name="return-type"></a>戻り値の型  
 **hierarchyid**  
  
## <a name="general-remarks"></a>全般的な解説  
 詳しくは、「 [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)」をご覧ください。  
  
## <a name="examples"></a>使用例  
 使用することができます、 **GetPathLocator**ファイル、ファイル サーバーから FileTable に移行するときに機能します。 このシナリオでは、ファイルを FileTable に移動した後、各ファイルの元の UNC パスを FileTable の UNC パスに置き換えます。 完全な例では、次を参照してください。 [Filetable にファイルを読み込む](../../relational-databases/blob/load-files-into-filetables.md)します。  
  
## <a name="see-also"></a>参照  
 [FileTable 内のディレクトリとパスの操作](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
