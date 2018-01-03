---
title: "DELETE タグ コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cf31107e21cee13d51046e43acc5c557cf20b9ee
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="delete-tag-command"></a>タグ コマンドを削除します。
複合インデックス (.cdx) ファイルからタグまたはタグを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>引数  
 *TagName1*の*CDXFileName1*[、 *TagName2*[OF *CDXFileName2*].  
 複合インデックス ファイルから削除するタグを指定します。 削除の 1 つのタグを持つ複数のタグを削除するには、コンマで区切られたタグ名の一覧を含みます。 同じ名前の 2 つ以上のタグは、開いているインデックス ファイルに存在する場合することができますタグを削除する特定のインデックス ファイルから OF を含めることによって*CDXFileName*です。  
  
 すべて [OF *CDXFileName*]  
 複合インデックス ファイルからすべてのタグを削除します。 現在のテーブルに、構造上の複合インデックス ファイルがある場合は、インデックス ファイルからすべてのタグが削除し、インデックス ファイルがディスクから削除フラグを関連付けられている構造の複合インデックス ファイルの存在を示す表のヘッダー内が削除されます。 すべてで使用する*CDXFileName*構造上の複合インデックスのファイル以外の複合インデックスを開いているファイルからすべてのタグを削除します。  
  
## <a name="remarks"></a>解説  
 インデックスを作成、複合インデックスのファイルには、インデックス エントリに対応するタグが含まれます。 タグの削除を使用して、複合インデックスを開いているファイルからタグまたはタグを削除します。 複合インデックスでのファイルを開く現在の作業領域タグのみを削除することができます。 複合インデックス ファイルからのすべてのタグを削除する場合は、ファイルがディスクから削除されます。  
  
 Visual FoxPro は構造の複合インデックス ファイル内のタグの最初の検索 (1 つは、開いている) 場合します。 タグがない場合、構造上の複合インデックス ファイルで、Visual FoxPro はし、他の複合インデックスを開いているファイルにタグを検索します。  
  
## <a name="see-also"></a>参照  
 [INDEX コマンド](../../odbc/microsoft/index-command.md)
