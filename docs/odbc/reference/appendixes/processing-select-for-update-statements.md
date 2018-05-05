---
title: UPDATE ステートメントの選択の処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ede999422f6b52112356aa7c9c4b7715eafb96c6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="processing-select-for-update-statements"></a>UPDATE ステートメントの選択の処理
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 相互運用性を最大にするため、アプリケーションが位置指定更新ステートメントを使用して実行することによって更新される結果セットを生成する必要があります、**更新用に選択**ステートメントです。 カーソル ライブラリでは、この必要はありません、位置指定の update ステートメントをサポートするほとんどのデータ ソースが必要です。  
  
 カーソル ライブラリ内の列を無視する、 **FOR UPDATE**の句、 **SELECT FOR UPDATE**ステートメントです。 ステートメントをドライバーに渡す前にこの句を削除します。 カーソル ライブラリで、前のセクションで説明した制限と共に、SQL_ATTR_CONCURRENCY ステートメント属性コントロール結果内の列を設定するかどうかを更新できます。
