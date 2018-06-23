---
title: Sqlgetdescfield による |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
caps.latest.revision: 51
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 23de7c344effa1093f75705f6dd0f2b27f852208
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164314"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、実装行記述子 (IRD) のみのドライバー固有の記述子フィールドを公開します。 IRD 内[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ドライバー固有の列の属性を通じて記述子フィールドが参照されます。 使用できるドライバー固有の記述子フィールドの完全な一覧については、次を参照してください。 [SQLColAttribute](sqlcolattribute.md)です。  
  
 列 ID 文字列を含む記述子フィールドは、多くの場合、長さが 0 の文字列になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有のすべての記述子フィールドの値は読み取り専用です。  
  
 SQLColAttribute では属性のようにレポート行レベルの属性 (SQL_CA_SS_COMPUTE_ID など) が、結果セット内のすべての列に対して報告される記述子フィールドを取得します。  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>SQLGetDescField とテーブル値パラメーター  
 Sqlgetdescfield によるは、テーブル値パラメーターおよびテーブル値パラメーター列の拡張属性の値を取得できます。 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>SQLGetDescField による機能強化された日付と時刻のサポート  
 新しい日付/時刻型で使用できる記述子フィールドについては、次を参照してください。[パラメーターと結果のメタデータ](../native-client-odbc-date-time/metadata-parameter-and-result.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、SQLGetDescField が返すことができます`SQL_C_SS_TIME2`(の`time`型) または`SQL_C_SS_TIMESTAMPOFFSET`(の`datetimeoffset`) の代わりに`SQL_C_BINARY`アプリケーションには、ODBC 3.8 が使用している場合、します。  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>SQLGetDescField による大きな CLR UDT のサポート  
 `SQLGetDescField` は、大きな CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>SQLGetDescField によるスパース列のサポート  
 Sqlgetdescfield によるは、新しい IRD フィールド SQL_CA_SS_IS_COLUMN_SET を確認するかどうか、列をクエリに使用できる、`column_set`列です。  
  
 詳細については、次を参照してください。[スパース列のサポート&#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)です。  
  
## <a name="example"></a>例  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>参照  
 [SQLGetDescField 関数](http://go.microsoft.com/fwlink/?LinkId=59351)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  