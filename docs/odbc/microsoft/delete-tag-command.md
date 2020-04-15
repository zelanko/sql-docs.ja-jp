---
title: タグ削除コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE TAG command [ODBC]
ms.assetid: 4f4e1362-a5f3-4b15-8a3c-d4e96605f221
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 97ca5abca7e70f5dffdae9bf14ce64429fd203d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303543"
---
# <a name="delete-tag-command"></a>DELETE TAG コマンド
複合インデックス (.cdx) ファイルからタグを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DELETE TAG TagName1 [OF CDXFileName1]  
   [, TagName2 [OF CDXFileName2]] ...  
  Or   
DELETE TAG ALL [OF CDXFileName]  
```  
  
## <a name="arguments"></a>引数  
 *タグ名1*の*CDX ファイル名1* *[, タグ名2*[OF *CDX ファイル名2]]*..  
 複合インデックス ファイルから削除するタグを指定します。 1 つの DELETE TAG で複数のタグを削除するには、コンマで区切ったタグ名のリストを含めます。 開いているインデックス ファイルに同じ名前のタグが複数存在する場合は、OF *CDXFileName*を含めることで、特定のインデックス ファイルからタグを削除できます。  
  
 すべて *[CDX ファイル名の*]  
 複合インデックス ファイルからすべてのタグを削除します。 現在のテーブルに構造複合インデックス ファイルがある場合、すべてのタグがインデックス ファイルから削除され、インデックス ファイルがディスクから削除され、関連する構造複合インデックス ファイルの存在を示すテーブルのヘッダーのフラグが削除されます。 構造複合インデックス ファイル以外のオープンな複合インデックス ファイルからすべてのタグを削除するには、ALL と OF *CDXFileName*を使用します。  
  
## <a name="remarks"></a>解説  
 INDEX で作成される複合インデックス ファイルには、インデックス エントリに対応するタグが含まれています。 DELETE TAG は、開いている複合インデックス ファイルからタグを削除するために使用されます。 現在の作業領域で開いている複合インデックスファイルからタグのみを削除できます。 複合インデックス ファイルからすべてのタグを削除すると、そのファイルはディスクから削除されます。  
  
 Visual FoxPro は、構造複合インデックス ファイル内のタグを最初に検索します (開いている場合)。 タグが構造複合インデックス ファイルにない場合、Visual FoxPro は、他の開いている複合インデックス ファイル内のタグを検索します。  
  
## <a name="see-also"></a>参照  
 [INDEX コマンド](../../odbc/microsoft/index-command.md)
