---
title: クライアントからサーバーへの変換を実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], client to server
ms.assetid: 6bb24928-0f3e-4119-beda-cfd04a44a3eb
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 155d6e55dac73df71fb25c388b9cd3af2360e9a7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076874"
---
# <a name="conversions-performed-from-client-to-server"></a>クライアントからサーバーへの変換
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB を使用して作成されたクライアント アプリケーションと [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) との間で実行される日付または時刻の変換について説明します。  
  
## <a name="conversions"></a>コンバージョン  
 このトピックでは、クライアントで行われる変換について説明します。 パラメーターに対して、サーバーで定義されているのとは異なる、秒の小数部の有効桁数をクライアントで指定した場合、サーバー側で変換すると処理に成功するのに、クライアント側で変換すると処理に失敗することがあります。 一方、クライアントで秒の小数部の切り捨てをエラーとして扱う具体的には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のラウンドの時間が最も近い全体の 2 番目の値。  
  
 場合と同様に DBTYPE_DBTIMESTAMP バインドを変換 icommandwithparameters::setparameterinfo を呼び出さない場合`datetime2`です。  
  
|変換先 -><br /><br /> From|DBDATE (date)|DBTIME (time)|DBTIME2 (time)|DBTIMESTAMP (smalldatetime)|DBTIMESTAMP (datetime)|DBTIMESTAMP (datetime2)|DBTIMESTAMPOFFSET (datetimeoffset)|STR|WSTR|SQLVARIANT<br /><br /> (sql_variant)|  
|----------------------|---------------------|---------------------|----------------------|-----------------------------------|------------------------------|-------------------------------|------------------------------------------|---------|----------|-------------------------------------|  
|[DATE]|1,2|1,3,4|4,12|1,12|1,12|1,12|1,5, 12|1,12|1,12|1,12<br /><br /> datetime2(0)|  
|DBDATE|1|-|-|1,6|1,6|1,6|1,5, 6|1,10|1,10|1<br /><br /> 日付|  
|DBTIME|-|1|1|1,7|1,7|1,7|1,5, 7|1,10|1,10|1<br /><br /> Time(0)|  
|DBTIME2|-|1,3|1|1,7,10,14|1,7,10,15|1,7,10|1,5,7,10|1,10,11|1,10,11|1<br /><br /> Time (7)|  
|DBTIMESTAMP|1,2|1,3,4|1,4,10|1,10,14|1,10,15|1,10|1,5,10|1,10,11|1,10,11|1,10<br /><br /> datetime2(7)|  
|DBTIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10,14|1,8,10,15|1,8,10|1,10|1,10,11|1,10,11|1,10<br /><br /> datetimeoffset(7)|  
|FILETIME|1,2|1,3,4|1,4,13|1,13|1,13|1,13|1,5,13|1,13|1,10|1,13<br /><br /> datetime2(3)|  
|BYTES|-|-|-|-|-|-|-|なし|なし|なし|  
|VARIANT|1|1|1|1,10|1,10|1,10|1,10|なし|なし|1,10|  
|SSVARIANT|1,16|1,16|1,16|1,10,16|1,10,16|1,10,16|1,10,16|なし|なし|1,16|  
|BSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|なし|なし|なし|  
|STR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|なし|なし|なし|  
|WSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|なし|なし|なし|  
  
## <a name="key-to-symbols"></a>記号の説明  
  
|シンボル|説明|  
|------------|-------------|  
|-|変換はサポートされていません。 Iaccessor::createaccessor が呼び出されたときに、バインドが検証されると、DBBINDSTATUS_UPSUPPORTEDCONVERSION がで返されます*rgStatus*です。 アクセサー検証が遅延する場合は、DBSTATUS_E_BADACCESSOR が設定されます。|  
|なし|該当なし。|  
|1|指定されたデータが有効でない場合、DBSTATUS_E_CANTCONVERTVALUE が設定されます。 入力データが検証されてから変換が適用されるので、コンポーネントは後続の変換で無視されることがあっても、変換を成功させるには有効である必要があります。|  
|2|時刻フィールドは無視されます。|  
|3|秒の小数部は 0 である必要があります。そうでなければ、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
|4|日付部分は無視されます。|  
|5|タイム ゾーンには、クライアントのタイム ゾーン設定が設定されます。|  
|6|時刻は 0 に設定されます。|  
|7|日付は現在の日付に設定されます。|  
|8|時刻は UTC に変換されます。 この変換中にエラーが発生した場合、DBSTATUS_E_CANTCONVERTVALUE が設定されます。|  
|9|文字列は ISO リテラルとして解析され、対象の型に変換されます。 これが失敗すると、文字列は OLE 日付リテラル (時刻要素も含む) として解析され、OLE Date (DBTYPE_DATE) から対象の型に変換されます。<br /><br /> 対象の型が DBTIMESTAMP、`smalldatetime`、`datetime`、または `datetime2` の場合、文字列は日付リテラル、時刻リテラル、または `datetime2` リテラルの構文か、OLE で認識される構文に準拠している必要があります。 文字列が日付リテラルの場合、すべての時刻部分が 0 に設定されます。 文字列が時刻リテラルの場合、日付は現在の日付に設定されます。<br /><br /> その他の対象の型の場合、文字列は対象の型のリテラルの構文に準拠している必要があります。|  
|10|データ損失を伴って秒の小数部が切り捨てられる場合、DBSTATUS_E_DATAOVERFLOW が設定されます。 文字列変換では、文字列が ISO 構文に準拠している場合のみオーバーフロー チェックが有効になります。 文字列が OLE 日付リテラルの場合、秒の小数部は丸められます。<br /><br /> DBTIMESTAMP (datetime) から smalldatetime への変換の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client は DBSTATUS_E_DATAOVERFLOW エラーは、秒の値を自動的に切り捨てられます。|  
|11|秒の小数点以下桁数は、次の表に従って、変換先の列のサイズによって決まります。 列のサイズが、テーブル内の範囲より大きい、小数点以下桁数は 9 桁と見なされます。 この変換では、秒の小数点以下桁数が 9 桁まで許容されます。これは、OLE DB で許容される最大桁数です。<br /><br /> ただし、変換元の型が DBTIMESTAMP で、秒の小数部が 0 の場合、秒の小数部または小数点は生成されません。 この動作により、以前の OLE DB プロバイダーを使用して開発されたアプリケーションの下位互換性が保証されます。<br /><br /> 列サイズが 0 より小さい場合は、OLE DB ではサイズが無制限であることを意味します (DBTIMESTAMP の 3 桁ルールが適用されなければ 9 桁)。<br /><br /> **DBTIME2** - 8, 10..18 (文字数); 0, 1..9 (小数点以下桁数)<br /><br /> **DBTIMESTAMP** - 19, 21..29 (文字数); 0, 1..9 (小数点以下桁数)<br /><br /> **DBTIMESTAMPOFFSET** - 26, 28..36 (文字数); 0, 1..9 (小数点以下桁数)|  
|12|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]DBTYPE_DATE に対するが保持されます。 秒の小数部は 0 に切り捨てられます。|  
|13|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]バージョンの DBTYPE_FILETIME に対するが保持されます。 Windows FileTimeToSystemTime API を使用する場合、秒の小数部の有効桁数は 1 ミリ秒に制限されます。|  
|14|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]の`smalldatetime`が保持されます。 秒は 0 に設定されます。|  
|15|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]の`datetime`が保持されます。 秒は、1/300 秒単位に丸められます。|  
|16|SSVARIANT クライアントの構造体に埋め込まれた (特定の型の) 値の変換動作は、SSVARIANT クライアントの構造体に埋め込まれていない場合の同一の値および型の動作と同じです。|  
  
## <a name="see-also"></a>参照  
 [バインドと変換&#40;OLE DB&#41;](conversions-ole-db.md)  
  
  