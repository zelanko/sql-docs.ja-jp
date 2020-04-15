---
title: VARCHAR カラム サイズ (オラクル用 ODBC ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11e1de3171521c57c80beb207d33e67d26d3e33
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304827"
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR 列のサイズ (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle8 では、VARCHAR カラムの最大サイズが 2000 バイトから 4000 バイトに増加しました。 Oracle 7.3.x クライアント ソフトウェアには、2000 バイトを超えるパラメータ値をバインドする方法はありません。 したがって、2000 バイトを超える VARCHAR 列を持つテーブルを作成すると、クライアント ソフトウェアの 2000 バイトの制限を超えるデータを使用して、パラメータ化された挿入、更新、削除、およびクエリを実行できなくなります。 Oracle 用 ODBC ドライバーと Oracle 用 OLE DB プロバイダーの両方がパラメーター化された挿入、更新、削除、およびクエリを使用するため、この場合、ORA-01026 エラーが報告されます。 Oracleクライアント・ソフトウェアによって適用される制限内にあるデータは機能します。 この 2000 バイトの制限を回避するには、クライアント ソフトウェアを Oracle8 (8.0.4.1.1c 以上) にアップグレードする必要があります。
