---
title: 強化された日付と時刻型 (OLE DB) のコピーの変更を一括 |Microsoft ドキュメント
description: 強化された日付と時刻型 (OLE DB) の一括コピーの変更
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, bulk copy operations
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 50917ad4c9d6184c32e8681c9b6bc455f5c61abc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bulk-copy-changes-for-enhanced-date-and-time-types-ole-db"></a>強化された日付と時刻型 (OLE DB) の一括コピーの変更
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  この記事では、SQL Server の OLE DB ドライバーの一括コピー機能をサポートするために日付/時刻の機能強化について説明します。  
  
## <a name="format-files"></a>フォーマット ファイル  
 フォーマット ファイルを対話形式で作成する場合に、日付型と時刻型の指定に使用する入力、および対応するホスト ファイル データ型名を次の表に示します。  
  
|ファイル ストレージ型|ホスト ファイル データ型|プロンプトへの応答:"フィールド < field_name > のファイル ストレージ型の入力 [\<既定 >]:"|  
|-----------------------|-------------------------|-----------------------------------------------------------------------------------------------------|  
|DateTime|SQLDATETIME|d|  
|Smalldatetime|SQLDATETIM4|D|  
|日付|SQLDATE|de|  
|[時刻]|SQLTIME|te|  
|Datetime2|SQLDATETIME2|d2|  
|Datetimeoffset|SQLDATETIMEOFFSET|do|  
  
 XML フォーマット ファイルの XSD への追加内容を次に示します。  
  
```  
<xs:complexType name="SQLDATETIME2">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATETIMEOFFSET">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLDATE">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="SQLTIME">  
    <xs:complexContent>  
        <xs:extension base="bl:Fixed"/>  
    </xs:complexContent>  
</xs:complexType>  
```  
  
## <a name="character-data-files"></a>文字データ ファイル  
 文字データ ファイルでは、日付と時刻の値の「データ形式: 文字列とリテラルをデータする"セクションで説明したとして表されます[OLE DB の日付と時刻の強化に対するデータ型のサポート](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)OLE DB 用です。  
  
 ネイティブ データ ファイルでは、4 つの新しい種類の日付と時刻の値は、小数点以下桁数 7 の TDS 表現として表されます (これは、最大でサポートされているため[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]し、bcp データ ファイルは、これらの列の小数点以下桁数を格納しないでください)。 既存の記憶域に変更がない**datetime**と**smalldatetime**型やその表形式データ ストリーム (TDS) の表現。  
  
 OLE DB の場合、さまざまなストレージ型のストレージ サイズは次のとおりです。  
  
|ファイル ストレージ型|ストレージ サイズ (バイト単位)|  
|-----------------------|---------------------------|  
|datetime|8|  
|smalldatetime|4|  
|date|3|  
|time|6|  
|datetime2|9|  
|datetimeoffset|11|  
 
  
## <a name="bcp-types-in-msoledbsqlh"></a>Msoledbsql.h 内の BCP 型  
 次の種類は、msoledbsql.h で定義されます。 これらの型がで渡される、 *eUserDataType* ibcpsession::bcpcolfmt OLE DB でのパラメーターです。  
  
|ファイル ストレージ型|ホスト ファイル データ型|Msoledbsql.h ibcpsession::bcpcolfmt で使用するために入力します。|値|  
|-----------------------|-------------------------|-----------------------------------------------------------|-----------|  
|DateTime|SQLDATETIME|BCP_TYPE_SQLDATETIME|0x3d|  
|Smalldatetime|SQLDATETIM4|BCP_TYPE_SQLDATETIM4|0x3a|  
|日付|SQLDATE|BCP_TYPE_SQLDATE|0x28|  
|[時刻]|SQLTIME|BCP_TYPE_SQLTIME|0x29|  
|Datetime2|SQLDATETIME2|BCP_TYPE_SQLDATETIME2|0x2a|  
|Datetimeoffset|SQLDATETIMEOFFSET|BCP_TYPE_SQLDATETIMEOFFSET|0x2b|  
  
## <a name="bcp-data-type-conversions"></a>BCP データ型変換  
 次の表に、変換情報を示します。  
  
 **OLE DB に関するメモ**IBCPSession によって、次の変換が実行されます。 IRowsetFastLoad で定義されている OLE DB 変換を使用して[クライアントからサーバーへの変換を実行](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)です。 次に示すクライアントでの変換が実行されると、datetime 値は 1/300 秒単位に丸められ、smalldatetime 値の秒は 0 に設定されます。 datetime の丸め処理は、時間と分に適用されますが、日付には適用されません。  
  
|変換先 --><br /><br /> From|date|time|smalldatetime|datetime|datetime2|datetimeoffset|char|wchar|  
|------------------------|----------|----------|-------------------|--------------|---------------|--------------------|----------|-----------|  
|日付|1|-|1、6|1、6|1、6|1、5、6|1、3|1、3|  
|[時刻]|なし|1、10|1、7、10|1、7、10|1、7、10|1、5、7、10|1、3|1、3|  
|Smalldatetime|1、2|1, 4, 10|1|1|1、10|1, 5, 10|1, 11|1, 11|  
|DateTime|1、2|1, 4, 10|1、12|1|1、10|1, 5, 10|1, 11|1, 11|  
|Datetime2|1、2|1, 4, 10|1、12|1、10|1、10|1, 5, 10|1、3|1、3|  
|Datetimeoffset|1、2、8|1、4、8、10|1, 8, 10|1, 8, 10|1, 8, 10|1、10|1、3|1、3|  
|Char/wchar (date)|9|-|9、6、12|9、6、12|9、6|9、5、6|なし|なし|  
|Char/wchar (time)|-|9、10|9、7、10、12|9、7、10、12|9、7、10|9、5、7、10|なし|なし|  
|Char/wchar (datetime)|9, 2|9, 4, 10|9、10、12|9、10、12|9、10|9、5、10|なし|なし|  
|Char/wchar (datetimeoffset)|9、2、8|9、4、8、10|9、8、10、12|9、8、10、12|9、8、10|9、10|なし|なし|  
  
#### <a name="key-to-symbols"></a>記号の説明  
  
|記号|意味|  
|------------|-------------|  
|-|変換はサポートされていません。<br />|  
|1|指定したデータが有効でない場合、エラーが通知されます。 datetimeoffset 値の場合は、UTC への変換が必要なくても、時刻部分は UTC への変換後の範囲内に収まっている必要があります。 TDS とサーバーは datetimeoffset 値の時刻を常に UTC 用に正規化するためです。 したがって、クライアントは、時刻部分が、UTC への変換後にサポートされる範囲内に収まっていることを確認する必要があります。|  
|2|時刻部分は無視されます。|  
|3|データ損失の切り捨てが発生した場合、エラーが通知されます。 datetime2 に関しては、次の表に示すように、秒の小数点以下桁数は変換先の列のサイズによって決まります。 列のサイズが、テーブル内の範囲より大きい、小数点以下桁数は 9 桁と見なされます。 この変換では、秒の小数点以下桁数が 9 桁まで許容されます。これは、OLE DB で許容される最大桁数です。<br /><br /> **型:** DBTIME2<br /><br /> **暗黙の小数点以下桁数 0** 8<br /><br /> **暗黙の小数点以下桁数 1..9** 1..9<br /><br /> <br /><br /> **型:** DBTIMESTAMP<br /><br /> **暗黙の小数点以下桁数 0:** 19<br /><br /> **暗黙の小数点以下桁数 1..9:** 21..29<br /><br /> <br /><br /> **型:** DBTIMESTAMPOFFSET<br /><br /> **暗黙の小数点以下桁数 0:** 26<br /><br /> **暗黙の小数点以下桁数 1..9:** 28..36|  
|4|日付部分は無視されます。|  
|5|タイム ゾーンは UTC (00:00 など) に設定されます。|  
|6|時刻は 0 に設定されます。|  
|7|日付は 1900-01-01 に設定されます。|  
|8|タイム ゾーン オフセットは無視されます。|  
|9|文字列が解析され、date、datetime、datetimeoffset、または最初に検出された句読点と残りのコンポーネントの有無によって、時刻の値に変換されます。 文字列がこの処理で検出されたソースの種類には、この記事の最後にテーブル内の規則に従って、対象の型に変換されます。 エラーを発生させずに提供されるデータを解析できない場合に、またはいずれかの部分が、許容範囲外の場合またはリテラルの型から対象の型への変換が存在しない場合は、エラーがポストされます。 Datetime および smalldatetime 型のパラメーターの年がこれらの種類がサポート範囲外の場合、エラーが通知されます。<br /><br /> datetimeoffset では、UTC への変換が必要なくても、値は UTC への変換後の範囲内に収まっている必要があります。 TDS とサーバーは datetimeoffset 値の時刻を常に UTC 用に正規化するので、クライアントは、時刻部分が、UTC への変換後にサポートされる範囲内に収まっていることを確認する必要があるためです。 値がサポートされている UTC の範囲内でない場合、エラーが通知されます。|  
|10|クライアント サーバー間の変換をデータ損失の切り捨てが発生した場合、エラーが通知されます。 サーバーが使用する UTC の範囲で表すことができる範囲の外に値がある場合にも、このエラーが発生します。 サーバーからクライアントへの変換で、秒または秒の小数部の切り捨てが行われた場合は、警告のみが発生します。|  
|11|クライアント サーバー間の変換をデータ損失の切り捨てが発生した場合、エラーが通知されます。|
|12|秒は 0 に設定され、秒の小数部は破棄されます。 切り捨てエラーは発生しません。|  
|なし|既存の [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以前のバージョンの動作が維持されます。|  
  
## <a name="see-also"></a>参照     
 [日付と時刻の強化 (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
