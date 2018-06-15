---
title: ストアド プロシージャを実行 odbc 呼び出しし、出力の処理 |Microsoft ドキュメント
description: プロセスのリターン コードと出力パラメーターの SQL Server の OLE DB Driver を使用します。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-how-to
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- ODBC CALL syntax
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 89e08882d06111e02057a95586c4f38c27b8db76
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665562"
---
# <a name="execute-stored-procedure-with-odbc-call-and-process-output"></a>ストアド プロシージャを実行 odbc 呼び出しし、出力の処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] のストアド プロシージャでは、整数のリターン コードと出力パラメーターを使用できます。 リターン コードと出力パラメーターはサーバーからの最後のパケットで送信されるため、行セットが完全に解放されるまでアプリケーションでは使用できません。 コマンドでは、複数の結果を返します、出力パラメーターのデータが使用可能な場合に**imultipleresults::getresult** DB_S_NORESULT を返すまたは**IMultipleResults**インターフェイスが完全に解放されると、先に生じた方です。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合、それらを暗号化する必要があります、 [Win32 Crypto API](http://go.microsoft.com/fwlink/?LinkId=64532)です。  
  
### <a name="to-process-return-codes-and-output-parameters"></a>リターン コードと出力パラメーターを処理するには  
  
1.  ODBC CALL エスケープ シーケンスを使用する SQL ステートメントを構築します。 このステートメントでは、各入出力パラメーター、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対してパラメーター マーカーを使用する必要があります。 入力パラメーターの場合は、パラメーター マーカーを使用するか、値をハード コーディングできます。  
  
2.  DBBINDING 構造体の配列を使用して、各パラメーター マーカーに 1 つずつ一連のバインドを作成します。  
  
3.  使用して、定義済みパラメーターのアクセサーを作成、 **iaccessor::createaccessor**メソッドです。 **CreateAccessor**バインドのセットからアクセサーを作成します。  
  
4.  DBPARAMS 構造体にデータを格納します。  
  
5.  呼び出す、 **Execute** (この場合は、呼び出しでストアド プロシージャに) コマンド。  
  
6.  行セットを処理しを使用してリリース、 **IRowset::Release**メソッドです。  
  
7.  ストアド プロシージャから受信したリターン コードと出力パラメーターの値を処理します。  
  
## <a name="example"></a>例  
 次の例は、行セット、リターン コード、および出力パラメーターの処理を示しています。 結果セットは処理されません。 このサンプルは IA64 ではサポートされていません。  
  
 このサンプルからダウンロードできる AdventureWorks サンプル データベースが必要です、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](http://go.microsoft.com/fwlink/?LinkID=85384)ホーム ページです。  
  
 1 つ目の ([!INCLUDE[tsql](../../../../includes/tsql-md.md)]) コード リストを実行して、アプリケーションで使用するストアド プロシージャを作成します。  
  
 ole32.lib と oleaut32.lib を使用して 2 つ目の (C++) コード リストをコンパイルし、実行します。 このアプリケーションは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] インスタンスに接続します。 一部の Windows オペレーティング システムをする必要があります変更 (localhost) または (local) の名前に、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]インスタンス。 名前付きインスタンスに接続する場合から、接続文字列を変更する"かに\\\name"という名前付きインスタンス。 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] Express は、既定で名前付きインスタンスとしてインストールされます。 INCLUDE 環境変数には、msoledbsql.h を格納するディレクトリが含まれています。 確認してください。  
  
 3 つ目の ([!INCLUDE[tsql](../../../../includes/tsql-md.md)]) コード リストを実行して、アプリケーションで使用したストアド プロシージャを削除します。  
  
```  
USE AdventureWorks  
if exists (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[myProc]'))  
   DROP PROCEDURE myProc  
GO  
  
CREATE PROCEDURE myProc   
    @inparam nvarchar(5),,  
    @outparam int OUTPUT  
  
AS  
SELECT Color, ListPrice   
FROM Production.Product WHERE Size > @inparam  
SELECT @outparam = 100  
  
IF  (@outparam > 0)  
    RETURN 999  
ELSE  
    RETURN 888  
GO  
```  
  
```  
// compile with: ole32.lib oleaut32.lib  
void InitializeAndEstablishConnection();  
  
#define UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <windows.h>  
#include <stdio.h>  
#include <stddef.h>  
#include <iostream>  
#include <oledb.h>  
#include <oledberr.h>  
#include <msoledbsql.h>  
  
using namespace std;  
  
IDBInitialize* pIDBInitialize = NULL;  
IDBCreateSession* pIDBCreateSession = NULL;  
IDBCreateCommand* pIDBCreateCommand = NULL;  
ICommandText* pICommandText = NULL;  
  
IRowset* pIRowset = NULL;  
ICommandWithParameters* pICommandWithParams = NULL;  
IAccessor* pIAccessor = NULL;  
IDBProperties* pIDBProperties = NULL;  
  
WCHAR* pStringsBuffer;  
DBBINDING* pBindings;  
const ULONG nInitProps = 4;  
DBPROP InitProperties[nInitProps];  
  
const ULONG nPropSet = 1;  
DBPROPSET rgInitPropSet[nPropSet];  
HRESULT hr;  
HACCESSOR hAccessor;  
  
const ULONG nParams = 3;   // Number of parameters in the command  
DBPARAMBINDINFO ParamBindInfo[nParams];  
ULONG i;  
ULONG cbColOffset = 0;  
  
ULONG ParamOrdinals[nParams];  
DBROWCOUNT cNumRows = 0;  
DBPARAMS Params;  
  
// Declare an array of DBBINDING structures, one for each parameter in the command.  
DBBINDING acDBBinding[nParams];  
DBBINDSTATUS acDBBindStatus[nParams];  
  
// The following buffer is used to store parameter values.  
typedef struct tagSPROCPARAMS {  
   long lReturnValue;  
   long outParam;  
   long inParam;  
} SPROCPARAMS;  
  
int main() {  
   // The command to execute.  
   WCHAR* wCmdString = L"{? = call myProc(?,?)}";  
  
   SPROCPARAMS sprocparams = {0,0,14};  
  
   // All the initialization activities in a separate function.  
   InitializeAndEstablishConnection();  
  
   // Create a new activity from the data source object.  
   if ( FAILED(pIDBInitialize->QueryInterface( IID_IDBCreateSession,   
      (void**) &pIDBCreateSession))) {  
         cout << "Failed to access IDBCreateSession interface.\n";  
         goto EXIT;  
   }  
   if (FAILED(pIDBCreateSession->CreateSession( NULL, IID_IDBCreateCommand,   
      (IUnknown**) &pIDBCreateCommand))) {  
         cout << "pIDBCreateSession->CreateSession failed.\n";  
      goto EXIT;  
   }  
  
   // Create a Command object.  
   if (FAILED(pIDBCreateCommand->CreateCommand(NULL, IID_ICommandText,   
      (IUnknown**) &pICommandText))) {  
         cout << "Failed to access ICommand interface.\n";  
         goto EXIT;  
   }  
  
   // Set the command text.  
   if (FAILED(pICommandText->SetCommandText(DBGUID_DBSQL, wCmdString))) {  
      cout << "Failed to set command text.\n";  
      goto EXIT;  
   }  
   // No need to describe command parameters (parameter name, data type  
   // etc) in DBPARAMBINDINFO structure and then SetParameterInfo(). The  
   // provider obtains this information by calling appropriate helper  
   // function.  
  
   // Describe the consumer buffer by filling in the array of DBBINDING structures.    
   // Each binding associates a single parameter to the consumer's buffer.  
   for ( i = 0 ; i < nParams ; i++ ) {  
      acDBBinding[i].obLength = 0;  
      acDBBinding[i].obStatus = 0;  
      acDBBinding[i].pTypeInfo = NULL;  
      acDBBinding[i].pObject = NULL;  
      acDBBinding[i].pBindExt = NULL;  
      acDBBinding[i].dwPart = DBPART_VALUE;  
      acDBBinding[i].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      acDBBinding[i].dwFlags = 0;  
      acDBBinding[i].bScale = 0;  
   }   // end for  
  
   acDBBinding[0].iOrdinal = 1;  
   acDBBinding[0].obValue = offsetof(SPROCPARAMS, lReturnValue);  
   acDBBinding[0].eParamIO = DBPARAMIO_OUTPUT;  
   acDBBinding[0].cbMaxLen = sizeof(long);  
   acDBBinding[0].wType = DBTYPE_I4;  
   acDBBinding[0].bPrecision = 11;  
  
   acDBBinding[1].iOrdinal = 2;  
   acDBBinding[1].obValue = offsetof(SPROCPARAMS, inParam);  
   acDBBinding[1].eParamIO = DBPARAMIO_INPUT;  
   acDBBinding[1].cbMaxLen = sizeof(long);  
   acDBBinding[1].wType = DBTYPE_I4;  
   acDBBinding[1].bPrecision = 11;  
  
   acDBBinding[2].iOrdinal = 3;  
   acDBBinding[2].obValue = offsetof(SPROCPARAMS, outParam);  
   acDBBinding[2].eParamIO = DBPARAMIO_OUTPUT;  
   acDBBinding[2].cbMaxLen = sizeof(long);  
   acDBBinding[2].wType = DBTYPE_I4;  
   acDBBinding[2].bPrecision = 11;  
  
   // Create an accessor from the above set of bindings.  
   hr = pICommandText->QueryInterface( IID_IAccessor, (void**)&pIAccessor);  
   if (FAILED(hr))  
      cout << "Failed to get IAccessor interface.\n";  
  
   hr = pIAccessor->CreateAccessor( DBACCESSOR_PARAMETERDATA,   
                                    nParams,         
                                    acDBBinding,   
                                    sizeof(SPROCPARAMS),   
                                    &hAccessor,  
                                    acDBBindStatus);  
   if (FAILED(hr))  
      cout << "Failed to create accessor for the defined parameters.\n";  
  
   // Fill in DBPARAMS structure for the command execution. This structure   
   // specifies the parameter values in the command and is then passed to Execute.  
   Params.pData = &sprocparams;  
   Params.cParamSets = 1;  
   Params.hAccessor = hAccessor;  
  
   // Execute the command.  
   if ( FAILED(hr = pICommandText->Execute( NULL,   
                                            IID_IRowset,   
                                            &Params,   
                                            &cNumRows,   
                                            (IUnknown **) &pIRowset))) {  
      cout << "Failed to execute command.\n";  
      goto EXIT;  
   }  
  
   printf("After command execution but before rowset processing.\n\n");  
   printf("  Return value = %d\n", sprocparams.lReturnValue);  
   printf("  Output parameter value = %d\n", sprocparams.outParam);  
   printf("  These are the same default values set in the application.\n\n\n");  
  
   // Result set is not important in this example; release it without processing.  
   pIRowset->Release();  
  
   printf("After processing the result set...\n");  
   printf("  Return value = %d\n", sprocparams.lReturnValue);  
   printf("  Output parameter value = %d\n\n", sprocparams.outParam);  
  
   // Release memory.  
   pIAccessor->ReleaseAccessor(hAccessor, NULL);  
   pIAccessor->Release();  
   pICommandText->Release();  
   pIDBCreateCommand->Release();  
   pIDBCreateSession->Release();      
   if (FAILED(pIDBInitialize->Uninitialize()))  
      // Uninitialize is not required, but it fails if an interface  
      // has not been released.  This can be used for debugging.  
      cout << "Problem uninitializing.\n";  
  
   pIDBInitialize->Release();  
  
   CoUninitialize();  
   return 0;  
  
EXIT:  
   if (pIAccessor != NULL)  
      pIAccessor->Release();  
   if (pICommandText != NULL)  
      pICommandText->Release();  
   if (pIDBCreateCommand != NULL)  
      pIDBCreateCommand->Release();  
   if (pIDBCreateSession != NULL)  
      pIDBCreateSession->Release();  
   if (pIDBInitialize != NULL)  
      if (FAILED(pIDBInitialize->Uninitialize()))  
         // Uninitialize is not required, but it fails if an  
         // interface has not been released.  This can be used for debugging.  
         cout << "Problem in uninitializing.\n";  
      pIDBInitialize->Release();  
  
   CoUninitialize();  
};  
  
void InitializeAndEstablishConnection() {      
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the OLE DB Driver for SQL Server.      
   hr = CoCreateInstance( CLSID_MSOLEDBSQL,   
                          NULL,   
                          CLSCTX_INPROC_SERVER,  
                          IID_IDBInitialize,   
                          (void **) &pIDBInitialize);  
   if (FAILED(hr))  
      cout << "Failed in CoCreateInstance().\n";  
  
   // Initialize the property values needed to establish the connection.  
   for ( i = 0 ; i < nInitProps ; i++ )  
      VariantInit(&InitProperties[i].vValue);  
  
   // Specify server name.  
   InitProperties[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt = VT_BSTR;  
  
   // Replace "MySqlServer" with proper value.  
   InitProperties[0].vValue.bstrVal = SysAllocString(L"(local)");  
   InitProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid = DB_NULLID;  
  
   // Specify database name.  
   InitProperties[1].dwPropertyID = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt = VT_BSTR;  
   InitProperties[1].vValue.bstrVal = SysAllocString(L"AdventureWorks");  
   InitProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid = DB_NULLID;  
  
   InitProperties[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt = VT_BSTR;  
   InitProperties[2].vValue.bstrVal = SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid = DB_NULLID;  
  
   // Now that properties are set, construct the DBPROPSET structure  
   // (rgInitPropSet).  The DBPROPSET structure is used to pass an array  
   // of DBPROP structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties = 4;  
   rgInitPropSet[0].rgProperties = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   if (FAILED(hr))  
      cout << "Failed to obtain IDBProperties interface.\n";  
  
   hr = pIDBProperties->SetProperties(nPropSet, rgInitPropSet);  
   if (FAILED(hr))  
      cout << "Failed to set initialization properties.\n";  
  
   pIDBProperties->Release();  
  
   // Now establish a connection to the data source.  
   if (FAILED(pIDBInitialize->Initialize()))  
      cout << "Problem in initializing.\n";  
}  
```  
  
```  
USE AdventureWorks  
DROP PROCEDURE myProc  
GO  
```  
  
## <a name="see-also"></a>参照  
 [結果を処理方法に関するトピック&#40;OLE DB&#41;](../../../oledb/ole-db-how-to/results/processing-results-how-to-topics-ole-db.md)  
  
  
