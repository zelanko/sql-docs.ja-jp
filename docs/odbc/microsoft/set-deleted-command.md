---
title: "削除されたコマンドの SET |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f3bf1ec522bee6fda19349a71c894ebd98bd75b9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="set-deleted-command"></a>SET DELETED コマンド
削除対象としてマークするレコードが処理されるかどうかおよびその他のコマンドで使用されるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 (ドライバーの既定値以外の場合は Visual FoxPro の既定値は OFF です。)記録 (関連するテーブルにレコードを含む) を処理するコマンドを示すレコードが削除対象としてマークを無視するスコープを使用して。  
  
 OFF  
 削除を記録 (関連するテーブルにレコードを含む) を操作するコマンドによってアクセスできますが、レコードに設定されていることを指定します、スコープを使用します。  
  
## <a name="remarks"></a>解説  
 削除に関するページ () で、テーブルのインデックスを作成する場合は、Visual FoxPro Rushmore テクノロジを使用してレコードの状態をテストする削除済み () の使用を最適化することができますを照会します。  
  
> [!IMPORTANT]  
>  削除設定には、コマンドの既定のスコープが現在のレコードの場合、または 1 つのレコードのスコープを含める場合は無視されます。 インデックスは常に削除設定を無視し、テーブル内のすべてのレコードのインデックスを作成します。  
  
## <a name="see-also"></a>参照  
 [SQL コマンドを削除します。](../../odbc/microsoft/delete-sql-command.md)
