---
title: SQLValidDSN 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbd8df72bcb0e76c8abcc3d738c2ff8da61a7bfe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039485"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN 関数
**互換性**  
 導入されたバージョン: ODBC 2.0  
  
 **まとめ**  
 **Sqlvaliddsn**は、システム情報に名前を追加する前に、データソース名の長さと有効性をチェックします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>引数  
 *lpszDSN*  
 代入確認するデータソース名。  
  
## <a name="returns"></a>戻り値  
 関数は、データソース名が有効である場合に TRUE を返します。 データソース名が無効な場合、または関数呼び出しが失敗した場合は、FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **Sqlvaliddsn**から FALSE が返された場合、 **sqlインストーラエラー**を呼び出すことによって、関連* \*する pferrorcode*値を取得できます。 データソース名が無効であるために FALSE が返された場合にのみ、関数呼び出しが失敗した場合にのみ、 * \*pferrorcode*が返されます。 次の表は、 **sqlインストーラエラー**によって返される可能性がある* \*pferrorcode*値と、この関数のコンテキストにおけるそれぞれの値を示しています。  
  
|*\*pfErrorCode*|エラー|[説明]|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般的なインストーラーエラー|特定のインストーラーエラーがなかったためにエラーが発生しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラーで関数を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **Sqlvaliddsn**は、データソース名の長さとデータソース名の個々の文字の有効性を確認するために、ドライバーの[configdsn](../../../odbc/reference/syntax/configdsn-function.md)によって呼び出されます。 名前の長さが SQL_MAX_DSN_LENGTH より大きいかどうかをチェックします。 Sqlext の定義に従ってください。 (データソース名の長さも[Sqlwritedsntoini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)によって確認されます)。**Sqlvaliddsn**は、次の無効な文字のいずれかがデータソース名に含まれているかどうかを確認します。  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|以下を参照してください。|  
|---------------------------|---------|  
|データソースの追加、変更、または削除|[Configdsn](../../../odbc/reference/syntax/configdsn-function.md) (セットアップ DLL 内)|  
|データソースの追加、変更、または削除|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|システム情報へのデータソース名の書き込み|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
