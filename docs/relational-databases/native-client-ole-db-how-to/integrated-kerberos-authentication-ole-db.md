---
title: 統合 Kerberos 認証 (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 953ee253-a4be-4f47-bbad-d2f6600207b2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 425850106e421e3fb763e3285a44f2894f39ef91
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694573"
---
# <a name="integrated-kerberos-authentication-ole-db"></a>統合 Kerberos 認証 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このサンプルでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client で、OLE DB を使用して、Kerberos 相互認証を行う方法を紹介しています。 このサンプルは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降で動作します。  
  
 Spn および Kerberos 認証の詳細については、次を参照してください。[サービス プリンシパル名&#40;SPN&#41;クライアント接続でサポート](../../relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections.md)です。  
  
## <a name="example"></a>例  
 サーバーを指定する必要があります。 .cpp ファイルで、"MyServer" の部分を [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のインスタンスが実行されているコンピューター名に変更してください。  
  
 また、顧客から提供された SPN を指定する必要があります。 .cpp ファイルで、"CPSPN" の部分を顧客から提供された SPN に変更してください。  
  
 INCLUDE 環境変数には、sqlncli.h に含まれているディレクトリが含まれています。 確認してください。 ole32.lib と oleaut32.lib を使用してコンパイルします。  
  
```  
// compile with: ole32.lib oleaut32.lib  
#pragma once  
  
#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlncli.h>  
  
#define CHECKHR(stmt) \  
   do { \  
      hr = (stmt); \  
      if (FAILED(hr)) { \  
         printf("CHECK_HR " #stmt " failed at (%hs, %d), hr=0x%08X\r\n", __FILE__, __LINE__, hr); \  
         goto CleanUp; \  
      } \  
   } while(0)  
  
#define CHECKVB(stmt) \  
   do { \  
      if ((stmt)!= VARIANT_TRUE) { \  
         printf("CHECK_VB " #stmt " failed at (%hs, %d)\r\n", __FILE__, __LINE__); \  
         goto CleanUp; \  
      } \  
   } while(0)  
  
#define CHECKBOOL(stmt) \  
   do { \  
      if (!(stmt)) { \  
         printf("CHECK_BOOL " #stmt " failed at (%hs, %d)\r\n", __FILE__, __LINE__); \  
        goto CleanUp; \  
      } \  
   } while(0)  
  
#define CHECKNULL(stmt) \  
   do { \  
      if ((stmt) == NULL) { \  
         printf("CHECK_NULL " #stmt " failed at (%hs, %d)\r\n", __FILE__, __LINE__); \  
         goto CleanUp; \  
      } \  
   } while(0)  
  
#define SAFERELEASE(p) \  
   do { \  
      if ((p)!= NULL) { \  
         p->Release(); \  
         p = NULL; \  
      } \  
   } while(0)  
  
#define SAFE_SYSFREESTRING(p) \  
   do { \  
      if ((p)!= NULL) { \  
         ::SysFreeString(p); \  
         p = NULL; \  
      } \  
   } while(0)  
  
int _tmain(int argc, _TCHAR* argv[]) {  
   HRESULT hr = S_OK;  
   IDBInitialize* pInitialize = NULL;  
   IDBProperties* pProperties = NULL;  
   DBPROPSET PropertySet[1];  
   DBPROP rgdbprop[1];  
   LPCWSTR lpwszProviderString = L"Server=MyServer;"   // server with SQL Server 2008 (or later)  
      L"Trusted_Connection=Yes;"  
      L"ServerSPN=CP_SPN;";   // customer-provided SPN  
   DBPROPID rgdbPropID[2];  
   DBPROPIDSET rgdbPropIDSet[1];  
   ULONG cPropertySets;  
   DBPROPSET *prgPropertySets;  
  
   CHECKHR(CoInitialize(NULL));  
   CHECKHR(CoCreateInstance(CLSID_SQLNCLI11, NULL, CLSCTX_INPROC_SERVER, __uuidof(IDBProperties), reinterpret_cast<void **>(&pProperties)));  
  
   // set provider string  
   rgdbprop[0].dwPropertyID = DBPROP_INIT_PROVIDERSTRING;  
   rgdbprop[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbprop[0].colid = DB_NULLID;  
   VariantInit(&(rgdbprop[0].vValue));  
   V_VT(&(rgdbprop[0].vValue)) = VT_BSTR;  
   V_BSTR(&(rgdbprop[0].vValue)) = SysAllocString(lpwszProviderString);  
  
   // set the property to the property set  
   PropertySet[0].rgProperties = &rgdbprop[0];  
   PropertySet[0].cProperties = 1;  
   PropertySet[0].guidPropertySet = DBPROPSET_DBINIT;  
  
   // set properties and connect to server  
   CHECKHR(pProperties->SetProperties(1, PropertySet));  
   CHECKHR(pProperties->QueryInterface(__uuidof(pInitialize), (void **)&pInitialize));  
   CHECKHR(pInitialize->Initialize());  
  
   // get properties  
   rgdbPropID[0] = SSPROP_INTEGRATEDAUTHENTICATIONMETHOD;  
   rgdbPropID[1] = SSPROP_MUTUALLYAUTHENTICATED;  
   rgdbPropIDSet[0].rgPropertyIDs = &rgdbPropID[0];  
   rgdbPropIDSet[0].cPropertyIDs = 2;  
   rgdbPropIDSet[0].guidPropertySet = DBPROPSET_SQLSERVERDATASOURCEINFO;  
  
   CHECKHR(pProperties->GetProperties(1, rgdbPropIDSet, &cPropertySets, &prgPropertySets));  
   wprintf(L"Authentication method: %s\r\n", (LPWSTR)V_BSTR(&(prgPropertySets[0].rgProperties[0].vValue)));  
   wprintf(L"Mutually authenticated: %s\r\n", (VT_BOOL == V_VT(&(prgPropertySets[0].rgProperties[1].vValue)))?L"yes":L"no");  
  
CleanUp:  
   SAFERELEASE(pProperties);  
   SAFERELEASE(pInitialize);  
  
   VariantClear(&(rgdbprop[0].vValue));  
   CoUninitialize();  
}  
```  
  
  
