---
title: VARCHAR 列のサイズ (ODBC Driver for Oracle) |Microsoft ドキュメント
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
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 02e02b9faf3bd19665536e141884bd663ad64266
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>VARCHAR 列のサイズ (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle8 で varchar 型の列の最大サイズは 4,000 バイトに 2000年からに増加しました。 Oracle 7.3.x クライアント ソフトウェアには、2000 のバイトを超えるパラメーター値をバインドすることはできません。 したがって、2000 のバイトを超えるの VARCHAR 列を含むテーブルを作成する場合はできないことがパラメーター化された挿入、更新、削除、および、クライアント ソフトウェアの 2000 バイトの制限を超えるデータとそれに対してクエリを実行します。 両方の Oracle 用の ODBC ドライバーと OLE DB Provider for Oracle は、パラメーター化された挿入、更新、削除、およびクエリを使用するため、エラーを報告または 01026 ここでします。 Oracle クライアント ソフトウェアによって適用される制限の範囲内のデータは動作します。 この 2000 バイトに制限を回避するのには、Oracle8 にクライアント ソフトウェアをアップグレードする必要があります (8.0.4.1.1c またはそれ以降)。
