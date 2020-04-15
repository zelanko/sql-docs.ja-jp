---
title: 時刻と日付の関数 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86260f8e7245bed15122d4dbfc4649131674e17f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303063"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>時刻および日付関数 (Visual FoxPro ODBC ドライバー)
次の表は、ビジュアル フォックスプロ ODBC ドライバーでサポートされている ODBC の時刻と日付の関数を一覧表示します。同じ関数の Visual FoxPro 文法が ODBC 構文と異なる場合は、対応するビジュアル FoxPro が一覧表示されます。  
  
|ODBC 文法|ビジュアルフォックスプロ文法|  
|------------------|---------------------------|  
|カーデート *( )*|日付 *( )*|  
|時間 *( )*|時間 *( )*|  
|曜日 *(date_exp)*|CDOW *(date_exp)*|  
|デイオブマンス *(date_exp)*|日 *( )*|  
|時間 *(time_exp)*||  
|分 *(time_exp)*||  
|月 *(time_exp)*||  
|月名 *(date_exp)*|ク月 *(date_exp)*|  
|今*すぐ ( )*|日時 *( )*|  
|セカンド *(time_exp)*|SEC *(time_exp)*|  
|週 *(date_exp)*||  
|年 *(date_exp)*||  
  
 次の日時関数はサポートされていません。  
  
 デイオブイヤー *(date_exp)*  
  
 四半期 *(date_exp)*  
  
 タイムスタンプ追加 *(間隔、integer_exp、timestamp_exp)*  
  
 タイムスタンプディフ *(間隔、timestamp_exp1、timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>ODBC エスケープ シーケンス  
 また、ドライバは日付データとタイムスタンプデータの ODBC エスケープシーケンスもサポートしています。 エスケープ句の構文は次のとおりです。  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 この構文では **、d**は*yyyy-mm-dd*形式の日付であることを示し **、ts**は*value**yyyy-mm-dd hh:mm:ss*のタイムスタンプであることを示します。 *value* *f.]* 形式。 日付とタイムスタンプのデータの短縮構文は次のとおりです。  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 例えば、以下の各ステートメントは、サポートされている SQL UPDATE コマンドで日付およびタイム・スタンプの短縮構文を使用して ALLTYPES 表を更新します。  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>解説  
 エスケープ シーケンスの詳細については、『ODBC プログラマ リファレンス』の[「ODBC でのエスケープ シーケンス](../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」を*参照してください*。
