---
title: "バージョン プロパティの例 (vc++) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Version property [ADO], VC++ example
ms.assetid: 2440b6ff-2536-497c-a5f4-41db0cf1945e
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 96ec6f8b7a30831b9150cdc63d7a21fb9eac8b8b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="version-property-example-vc"></a>バージョン プロパティの例 (vc++)
この例では、[バージョン](../../../ado/reference/ado-api/version-property-ado.md)のプロパティ、[接続](../../../ado/reference/ado-api/connection-object-ado.md)ADO の現在のバージョンを表示するオブジェクト。 表示するいくつかの動的なプロパティを使用します。  
  
-   現在の DBMS 名とバージョンです。  
  
-   OLE DB バージョンです。  
  
-   プロバイダー名とバージョン。  
  
-   ODBC のバージョンです。  
  
-   ODBC ドライバー名およびバージョンです。  
  
> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]**または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。  
  
```  
// BeginVersionCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void VersionX();  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
    if (FAILED(::CoInitialize(NULL)))  
        return -1;  
  
    VersionX();  
  
    ::CoUninitialize();  
}  
  
void VersionX() {  
    HRESULT hr = S_OK;  
  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
    // Define ADO object pointers.  Initialize pointers on define.  
    // These are in the ADODB::  namespace.  
    _ConnectionPtr pConnection = NULL;  
  
    try {  
        // Open connection.  
        TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
        pConnection->Open (strCnn, "", "", adConnectUnspecified);  
  
        printf("ADO Version   : %s\n\n",(LPCSTR) pConnection->Version);  
        printf("DBMS Name   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("DBMS Name")->Value);  
        printf("DBMS Version   : %s\n\n",(LPCSTR) (_bstr_t)  
            pConnection->Properties->GetItem("DBMS Version")->Value);  
        printf("OLE DB Version   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("OLE DB Version")->Value);  
        printf("Provider Name   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("Provider Name")->Value);  
        printf("Provider Version   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("Provider Version")->Value);  
        printf("Driver Name   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("Driver Name")->Value);  
        printf("Driver Version   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("Driver Version")->Value);  
        printf("Driver ODBC Version   : %s\n\n",(LPCSTR) (_bstr_t)   
            pConnection->Properties->GetItem("Driver ODBC Version")->Value);  
  
    }  
  
    catch (_com_error &e) {  
        // Notify the user of errors if any.  
        PrintProviderError(pConnection);  
        PrintComError(e);  
    }  
  
    if (pConnection)  
        if (pConnection->State == adStateOpen)  
            pConnection->Close();  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
    // Print Provider Errors from Connection object.  
    // pErr is a record object in the Connection's Error collection.  
    ErrorPtr pErr = NULL;  
  
    if ( (pConnection->Errors->Count) > 0) {  
        long nCount = pConnection->Errors->Count;  
        // Collection ranges from 0 to nCount -1.  
        for ( long i = 0 ; i < nCount ; i++) {  
            pErr = pConnection->Errors->GetItem(i);  
            printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
        }  
    }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
    // Print Com errors.  
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>参照  
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Version プロパティ (ADO)](../../../ado/reference/ado-api/version-property-ado.md)
