---
title: 集計関数、CALC 関数と NEW キーワード |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], functions
- CALC function [ADO]
- NEW keyword [ADO]
- aggregate functions [ADO]
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba6aae19a559dd1e475809339281c8b65c282517
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271551"
---
# <a name="aggregate-functions-the-calc-function-and-the-new-keyword"></a>集計関数、CALC 関数と NEW キーワード
データ シェイプには、次の関数がサポートされています。 処理される列を含む章に割り当てられた名前が、*章エイリアス*です。  
  
 チャプター エイリアスを完全修飾である章に先行するそれぞれの章列名から成るにあることができます、*列名、* ピリオドで区切っています。 たとえば、親章、chap1、子の章では、chap2 に含まれる場合 amt、amount 列を含む、修飾名 chap1.chap2.amt です。  
  
|集計関数|説明|  
|-------------------------|-----------------|  
|SUM (*章エイリアス*.*列名*)|指定された列のすべての値の合計を計算します。|  
|AVG (*章エイリアス*.*列名*)|指定された列のすべての値の平均を計算します。|  
|MAX (*章エイリアス*.*列名*)|指定された列の最大値を計算します。|  
|MIN (*章エイリアス*.*列名*)|指定された列内の最小値を計算します。|  
|カウント (*章エイリアス*[.*列名*])|指定したエイリアスの行数をカウントします。 列が指定されている場合は、カウントにその列の Null 以外のみの行が含まれます。|  
|STDEV (*章エイリアス*.*列名*)|指定された列の標準偏差を計算します。|  
|ANY (*章エイリアス*.*列名*)|指定された列の値です。 予測可能な値は、列の値はチャプター内のすべての行の同じ場合にのみいずれかが存在します。<br /><br /> **注**列にチャプター内の行のすべてに対して同じ値が含まれていない場合、図形コマンド任意を返します、関数の値を指定する値のいずれか。|  
  
|計算式|説明|  
|---------------------------|-----------------|  
|CALC(*expression*)|ただし、に対してのみの行の任意の式を計算、**レコード セット**CALC 関数を含むです。 これらを使用して任意の式[の Visual Basic for Applications (VBA) 関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)は許可されています。|  
  
|NEW キーワード|説明|  
|-----------------|-----------------|  
|NEW *フィールド型*[(*幅*&#124;*スケール*&#124;*精度*&#124;*エラー* [、*スケール*&#124;*エラー*])]|指定した型の空の列を追加、 **Recordset**です。|  
  
 *フィールド型*NEW キーワードと共に渡されるとデータ型を次のいずれかが指定できます。  
  
|OLE DB データ型|ADO データ型の equivalent(s)|  
|-----------------------|-----------------------------------|  
|DBTYPE_BSTR|adBSTR|  
|DBTYPE_BOOL|adBoolean|  
|DBTYPE_DECIMAL|adDecimal|  
|DBTYPE_UI1|adUnsignedTinyInt|  
|DBTYPE_I1|adTinyInt|  
|DBTYPE_UI2|adUnsignedSmallInt|  
|DBTYPE_UI4|adUnsignedInt|  
|DBTYPE_I8|adBigInt|  
|DBTYPE_UI8|adUnsignedBigInt|  
|DBTYPE_GUID|adGuid|  
|DBTYPE_BYTES|adBinary、AdVarBinary、adLongVarBinary|  
|DBTYPE_STR|adChar、adVarChar、adLongVarChar|  
|DBTYPE_WSTR|adWChar、adVarWChar、adLongVarWChar|  
|DBTYPE_NUMERIC|adNumeric|  
|DBTYPE_DBDATE|adDBDate|  
|DBTYPE_DBTIME|adDBTime|  
|DBTYPE_DBTIMESTAMP|adDBTimeStamp|  
|DBTYPE_VARNUMERIC|adVarNumeric|  
|DBTYPE_FILETIME|adFileTime|  
|DBTYPE_ERROR|adError|  
  
 10 進数の (OLE DB DBTYPE_DECIMAL、または ADO では、adDecimal) 型の新しいフィールドがある場合は、有効桁数と小数点以下桁数の値を指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
