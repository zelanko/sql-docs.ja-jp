---
title: 日付と時刻の強化 |Microsoft ドキュメント
description: SQL Server 用に OLE DB ドライバーの日付と時刻の機能強化
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d6b287b7cf96ec91ce776dd65bcec01e8c777a1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="date-and-time-improvements"></a>日付と時刻の強化
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ここで、OLE DB Driver for SQL Server に追加された日付と時刻のデータ型のサポートについて説明[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]です。  
  
 日付/時刻の強化の詳細については、次を参照してください。[日付と時刻の強化&#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)です。  
  
 この機能を説明するサンプル アプリケーションについては、次を参照してください。 [SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)です。  
  
## <a name="usage"></a>使用方法  
 ここでは、新しい日付型と時刻型のさまざまな使用方法について説明します。  
  
### <a name="use-date-as-a-distinct-data-type"></a>個別のデータ型として日付を使用する  
 以降で[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]日付/時刻型のサポートの強化によりより効果的に DBTYPE_DBDATE OLE DB 型を使用します。  
  
### <a name="use-time-as-a-distinct-data-type"></a>個別のデータ型として時刻を使用する  
 OLE DB には既に、有効桁数が 1 秒のデータ型として DBTYPE_DBTIME があります。このデータ型には時刻のみが含まれます。
  
 新しい[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]時刻データ型は小数秒の精度が 100 ナノ秒です。 SQL Server の OLE DB ドライバーの新しい型が必要です: DBTYPE_DBTIME2 です。 秒の小数部を含まない時刻を使用するように記述された既存のアプリケーションでは、time(0) 列を使用できます。 既存の OLE DB DBTYPE_TIME 型とその対応する構造体は必要がありますアプリケーションは、メタデータに返される型に依存しない限り、正しく機能します。  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>秒の有効桁数が拡張された個別のデータ型として時刻を使用する  
 プロセス制御や製造アプリケーションなど、アプリケーションによっては、有効桁数が 100 ナノ秒までの時刻データを処理できる必要があります。 OLE DB では、この目的のための新しい種類は、DBTYPE_DBTIME2 です。  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>秒の有効桁数が拡張された Datetime を使用する  
 OLE DB では既に、有効桁数が 1 ナノ秒までの型が定義されています。 ただし、この型は既に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既存のアプリケーションで使用されており、このようなアプリケーションでは、有効桁数を 1/300 秒までしか想定していません。 新しい**datetime2(3)** 型は、既存の datetime 型と直接的な互換性はありません。 これがアプリケーションの動作に影響するというリスクがある場合、アプリケーションは新しい DBCOLUMN フラグを使用して、実際のサーバーの種類を判断する必要があります。    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>秒の有効桁数とタイム ゾーンが拡張された Datetime を使用する  
 アプリケーションによっては、タイム ゾーン情報を含む datetime 値が必要です。 これは、新しい DBTYPE_DBTIMESTAMPOFFSET 種類でサポートされています。
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>既存の変換と一貫性のあるクライアント側変換で Date/Time/Datetime/Datetimeoffset データを使用する  
 導入された、すべての日付と時刻型の間の変換を含める一貫した方法で、変換は拡張[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
