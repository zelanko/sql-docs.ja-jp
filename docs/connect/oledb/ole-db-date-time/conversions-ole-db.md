---
title: バインドと変換 (OLE DB) |Microsoft ドキュメント
description: バインドと変換 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6bff4cdd5ea1a6b2fef3283ba9c0413e3d26842
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="conversions-ole-db"></a>変換 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  このセクションでは、の間で変換する方法を説明**datetime**と**datetimeoffset**値。 ここで説明する変換は、OLE DB によって既に提供されているか、OLE DB の一貫性がある拡張機能です。  
  
 OLE DB における日付と時刻のリテラルと文字列の形式は、通常 ISO に従うため、クライアントのロケールに依存しません。 これには、標準が OLE オートメーションである DBTYPE_DATE という例外があります。 ただし、OLE DB Driver for SQL Server のみでに変換するか、クライアントからのデータが送信するときの型の間であるため、アプリケーションを強制的に OLE DB Driver for SQL Server に DBTYPE_DATE と文字列の形式の間で変換する方法はありません。 それ以外の場合、文字列では次の形式を使用します (角かっこに囲まれたテキストは省略可能な要素を示します)。  
  
-   形式**datetime**と**datetimeoffset**文字列は。  
  
     *yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ± *hh*:*mm*]]  
  
-   形式**時間**文字列は。  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   形式**日付**文字列は。  
  
     *yyyy*-*mm*-*dd*  
  
> [!NOTE]  
>  以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client および SQLOLEDB では、標準の変換が失敗した場合に備えて OLE 変換が実装されていました。 SQL Server の OLE DB ドライバーと同じ動作に依存して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client です。 その結果、SQL Server の OLE DB ドライバーによって実行されるいくつかの変換は、OLE DB 仕様によって異なります。  
  
 文字列からの変換では、空白文字やフィールドの幅を柔軟に処理できます。 詳細についてを参照してください「データ形式: 文字列とリテラルをデータする」 [OLE DB の日付と時刻の強化に対するデータ型のサポート](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)です。  
  
 一般的な変換規則を次に示します。  
  
-   文字列を日付型または時刻型に変換すると、文字列はまず ISO リテラルとして解析されます。 これが失敗すると、文字列は OLE 日付リテラルとして解析されます。OLE 日付リテラルには時刻要素があります。  
  
-   時刻が存在しなくても受信側が時刻を格納できる場合、時刻は 0 に設定されます。 日付が存在しなくても受信側が日付を格納できる場合、ISO 変換を使用すると日付は現在の日付に設定され、OLE 変換を使用すると日付は 1899-12-30 に設定されます。  
  
-   クライアントが使用しているデータ型にタイム ゾーンが存在しなくても、サーバーがタイム ゾーンを格納できる場合、クライアントのデータはクライアントのタイム ゾーンで表されていると仮定されます。  
  
-   サーバーにタイム ゾーンが存在しなくても、クライアントにタイム ゾーン情報がある場合、UTC のタイム ゾーンが使用されます。 これはサーバーの動作とは異なります。  
  
-   時刻が存在しても受信側が時刻を格納できない場合、時刻要素は無視されます。  
  
-   日付が存在しても受信側が日付を格納できない場合、日付要素は無視されます。  
  
-   クライアントからサーバーへの変換時に秒または秒の小数部の切り捨てが発生すると、DB_E_ERRORSOCCURRED が返され、状態 DBSTATUS_E_DATAOVERFLOW が設定されます。  
  
-   サーバーからクライアントへの変換時に秒または秒の小数部の切り捨てが発生すると、DBSTATUS_S_TRUNCATED が設定されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クライアントからサーバーへの変換](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)  
 間で実行される日付/時刻変換をについて説明します。 SQL Server の OLE DB ドライバーで作成されたクライアント アプリケーションと[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](またはそれ以降)。  
  
 [サーバーからクライアントへの変換](../../oledb/ole-db-date-time/conversions-performed-from-server-to-client.md)  
 間で実行される日付/時刻の変換について説明[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](またはそれ以降) と SQL Server の OLE DB ドライバーで作成されたクライアント アプリケーション。  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
