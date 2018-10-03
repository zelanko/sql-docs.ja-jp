---
title: SET DELETED コマンド |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5efbd7e98b430128e52634f5c7d71597afc89ace
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806070"
---
# <a name="set-deleted-command"></a>SET DELETED コマンド
削除対象としてマークするレコードを処理するかどうかおよびその他のコマンドで使用されるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 ドライバーの既定値 (Visual FoxPro の既定値は OFF)。(関連するテーブルにレコードを含む) のレコードを操作するコマンドを指定します。 削除対象としてマークするレコードを無視するスコープを使用します。  
  
 OFF  
 削除 (関連付けられたテーブル内のレコードを含む) のレコードを操作するコマンドがアクセスできるが、レコードにマークされていることを指定します。 スコープを使用します。  
  
## <a name="remarks"></a>コメント  
 テーブルが削除された () でインデックス付けされた場合は、Visual FoxPro Rushmore テクノロジを使用してレコードの状態をテストする削除済み () の使用を最適化することができますを照会します。  
  
> [!IMPORTANT]  
>  コマンドの既定のスコープが現在のレコードの場合、または 1 つのレコードのスコープを含める場合は、削除の設定は無視されます。 常に、インデックスは削除設定を無視し、テーブル内のすべてのレコードのインデックスを作成します。  
  
## <a name="see-also"></a>参照  
 [DELETE - SQL コマンド](../../odbc/microsoft/delete-sql-command.md)
