---
title: DDL ステートメント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cae06efe6dd11e651e8553fa5c1004c2fa145478
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302993"
---
# <a name="ddl-statements"></a>DDL ステートメント
データ定義言語 (DDL) ステートメントは、DBMS 間で大きく異なります。 ODBC SQL では、最も一般的なデータ定義操作のステートメント (テーブル、インデックス、およびビューの作成と削除) が定義されます。テーブルを変更する。特権の付与と取り消しを行います。 その他の DDL ステートメントはすべて、データ ソース固有です。 したがって、相互運用可能なアプリケーションでは、一部のデータ定義操作を実行できません。 一般的に、このような操作は DBMS に特化する傾向があり、ほとんどの DBMS に付属する専用のデータベース管理ソフトウェアやドライバに付属のセットアップ プログラムに任せられるのが最善であるため、これは問題ではありません。  
  
 データ定義のもう 1 つの問題は、データ・タイプ名が DBMS 間で大きく異なっている点です。 **SQLGetTypeInfo**は、標準のデータ型名を定義して、強制的に DBMS 固有の名前に変換するドライバではなく、アプリケーションが DBMS 固有のデータ型名を検出する方法を提供します。 相互運用可能なアプリケーションでは、SQL ステートメントでこれらの名前を使用して、テーブルを作成および変更する必要があります。[「付録 C : SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」および「付録[D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」に記載されている名前は、その一例にすぎません。
