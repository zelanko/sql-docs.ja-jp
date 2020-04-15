---
title: 更新ステートメントの選択の処理 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], select for update statements
- select for update [ODBC]
- SQL statements [ODBC], cursor library
- cursor library [ODBC], select for update statements
- ODBC cursor library [ODBC], select for update statements
- cursor library [ODBC], statement processing
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 904028cd7b3798fcac8f9e5afa6186fae3e9fa29
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81308013"
---
# <a name="processing-select-for-update-statements"></a>SELECT FOR UPDATE ステートメントの処理
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 相互運用性を最大限に高めるには、アプリケーションは**SELECT FOR UPDATE**ステートメントを実行して位置指定更新ステートメントで更新される結果セットを生成する必要があります。 カーソル ライブラリではこの必要はありませんが、位置指定更新ステートメントをサポートするほとんどのデータ ソースで必要とされます。  
  
 カーソル ライブラリは **、SELECT** FOR **UPDATE**ステートメントの FOR UPDATE 句の列を無視します。この句は、ステートメントをドライバーに渡す前に削除されます。 カーソル ライブラリでは、SQL_ATTR_CONCURRENCY ステートメント属性と、前のセクションで説明した制限と共に、結果セット内の列を更新できるかどうかを制御します。
