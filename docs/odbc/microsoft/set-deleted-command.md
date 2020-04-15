---
title: 削除コマンドを設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b3302dc7eecca7135dab9dff5afa376169be0f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300882"
---
# <a name="set-deleted-command"></a>SET DELETED コマンド
削除対象としてマークされたレコードを処理するかどうか、および他のコマンドで使用できるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値、ビジュアル FoxPro の既定値はオフです)。有効範囲を使用してレコード (関連テーブルのレコードを含む) を操作するコマンドが、削除対象としてマークされたレコードを無視することを指定します。  
  
 OFF  
 削除対象としてマークされたレコードに、スコープを使用してレコード (関連テーブルのレコードを含む) を操作するコマンドがアクセスできるように指定します。  
  
## <a name="remarks"></a>解説  
 DELETED( ) を使用してレコードの状態をテストするクエリは、テーブルが DELETED( ) でインデックス付けされている場合、ビジュアル FoxPro ラッシュモア テクノロジを使用して最適化できます。  
  
> [!IMPORTANT]  
>  SET DELETED は、コマンドのデフォルトの有効範囲が現行レコードである場合、または単一レコードの有効範囲を含む場合は無視されます。 INDEX は常に SET DELETED を無視し、テーブル内のすべてのレコードにインデックスを付けます。  
  
## <a name="see-also"></a>参照  
 [DELETE - SQL コマンド](../../odbc/microsoft/delete-sql-command.md)
