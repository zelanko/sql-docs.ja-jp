---
title: RPC でのストアド プロシージャの実行と処理の出力 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- RPC syntax
- stored procedures [SQL Server], RPC syntax
ms.assetid: 1eb60087-da67-433f-9b45-4028595e68ab
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e04bac0098832cf172b3a991f121d262fc128220
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427921"
---
# <a name="execute-stored-procedure-with-rpc-and-process-output"></a>RPC でのストアド プロシージャの実行と処理の出力
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のストアド プロシージャでは、整数のリターン コードと出力パラメーターを使用できます。 リターン コードと出力パラメーターはサーバーからの最後のパケットで送信されるため、行セットが完全に解放されるまでアプリケーションでは使用できません。 コマンドが複数の結果を返す場合の出力パラメーター データが使用可能な場合に**imultipleresults::getresult** DB_S_NORESULT を返す場合、または、 **IMultipleResults**インターフェイスが完全には早い方を公開しました。  
  
> [!IMPORTANT]  
>  可能な場合は、Windows 認証を使用します。 Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。 資格情報をファイルに保存するのは避けてください。 資格情報を保持する必要がある場合、それらを暗号化する必要があります、 [Win32 Crypto API](http://go.microsoft.com/fwlink/?LinkId=64532)します。  
  
### <a name="to-process-return-codes-and-output-parameters"></a>リターン コードと出力パラメーターを処理するには  
  
1.  RPC エスケープ シーケンスを使用する SQL ステートメントを作成します。  
  
2.  呼び出す、 **icommandwithparameters::setparameterinfo**メソッドにパラメーターをプロバイダーについて説明します。 PARAMBINDINFO 構造体の配列にパラメーター情報を格納します。  
  
3.  セットを作成 DBBINDING 構造体の配列を使用して、バインド (各パラメーター マーカーに 1 つ)。  
  
4.  使用して、定義済みパラメーターのアクセサーを作成、 **iaccessor::createaccessor**メソッド。 **CreateAccessor**バインドのセットからアクセサーを作成します。  
  
5.  DBPARAMS 構造体にデータを格納します。  
  
6.  呼び出す、 **Execute** (この場合は、呼び出しでストアド プロシージャに) コマンド。  
  
7.  行セットを処理し、リリースを使用して、 **irowset::release**メソッド。  
  
8.  ストアド プロシージャから受信したリターン コードと出力パラメーターの値を処理します。  
  
## <a name="example"></a>例  
 次の例は、行セット、リターン コード、および出力パラメーターの処理を示しています。 結果セットは処理されません。 このサンプルは IA64 ではサポートされていません。  
  
 このサンプルからダウンロードできる AdventureWorks サンプル データベースが必要です、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](http://go.microsoft.com/fwlink/?LinkID=85384)ホーム ページ。  
  
 1 つ目の ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード リストを実行して、アプリケーションで使用するストアド プロシージャを作成します。  
  
 ole32.lib と oleaut32.lib を使用して 2 つ目の (C++) コード リストをコンパイルし、実行します。 このアプリケーションは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに接続します。 Windows オペレーティング システムによっては、必要がありますを変更 (localhost) または (local) の名前に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス。 を名前付きインスタンスに接続するから、接続文字列を変更"するか\\\name"名は名前付きインスタンスです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Express は、既定で名前付きインスタンスとしてインストールされます。 INCLUDE 環境変数には、sqlncli.h を含むディレクトリが含まれています。 を確認します。  
  
 3 つ目の ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) コード リストを実行して、アプリケーションで使用したストアド プロシージャを削除します。  
  
```  
USE AdventureWorks  
if exists (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[myProc]'))  
   DROP PROCEDURE myProc  
GO  
  
CREATE PROCEDURE myProc   
    @inparam nvarchar(5),  
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
#include <SQLNCLI.h>  
  
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
  
DB_UPARAMS ParamOrdinals[nParams];  
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
   // WCHAR* wCmdString = L"{? = call myProc(?,?)}";  
   WCHAR* wCmdString = L"{rpc myProc}";  
   SPROCPARAMS sprocparams = {0,0,14};  
  
   // All the initialization activities in a separate function.  
   InitializeAndEstablishConnection();  
  
   // Create a new activity from the data source object.  
   if (FAILED(pIDBInitialize->QueryInterface(IID_IDBCreateSession,   
                                             (void**) &pIDBCreateSession))) {  
      cout << "Failed to access IDBCreateSession interface.\n";  
      goto EXIT;  
   }  
  
   if ( FAILED(pIDBCreateSession->CreateSession( NULL, IID_IDBCreateCommand,   
                                                (IUnknown**) &pIDBCreateCommand))) {  
      cout << "pIDBCreateSession->CreateSession failed.\n";  
      goto EXIT;  
   }  
  
   // Create a Command object.  
   if (FAILED(pIDBCreateCommand->CreateCommand( NULL,         
                                                IID_ICommandText,   
                                                (IUnknown**) &pICommandText))) {  
      cout << "Failed to access ICommand interface.\n";  
      goto EXIT;  
   }  
  
   // Set the command text.  
   if (FAILED(pICommandText->SetCommandText(DBGUID_DBSQL, wCmdString))) {  
      cout << "Failed to set command text.\n";  
      goto EXIT;  
   }  
  
   // Describe the command parameters (parameter name, provider specific name of  
   // the parameter's data type, and so on.) in an array of DBPARAMBINDINFO   
   // structures.  This information is then used by SetParameterInfo().  
   ParamBindInfo[0].pwszDataSourceType = L"DBTYPE_I4";  
   ParamBindInfo[0].pwszName = L"@ReturnVal";   // return value from sp  
   ParamBindInfo[0].ulParamSize = sizeof(long);  
   ParamBindInfo[0].dwFlags = DBPARAMFLAGS_ISOUTPUT;  
   ParamBindInfo[0].bPrecision = 11;  
   ParamBindInfo[0].bScale = 0;  
   ParamOrdinals[0] = 1;  
  
   ParamBindInfo[1].pwszDataSourceType = L"DBTYPE_I4";  
   ParamBindInfo[1].pwszName = L"@inparam";  
   ParamBindInfo[1].ulParamSize = sizeof(long);  
   ParamBindInfo[1].dwFlags = DBPARAMFLAGS_ISINPUT;  
   ParamBindInfo[1].bPrecision = 11;  
   ParamBindInfo[1].bScale = 0;  
   ParamOrdinals[1] = 2;  
  
   ParamBindInfo[2].pwszDataSourceType = L"DBTYPE_I4";  
   ParamBindInfo[2].pwszName = L"@outparam";  
   ParamBindInfo[2].ulParamSize = sizeof(long);  
   ParamBindInfo[2].dwFlags = DBPARAMFLAGS_ISOUTPUT;  
   ParamBindInfo[2].bPrecision = 11;  
   ParamBindInfo[2].bScale = 0;  
   ParamOrdinals[2] = 3;  
  
   //Set the parameters information.  
   if ( FAILED(pICommandText->QueryInterface( IID_ICommandWithParameters,  
                                            (void**)&pICommandWithParams))) {  
      cout << "Failed to obtain ICommandWithParameters.\n";  
      goto EXIT;  
   }  
  
   if ( FAILED(pICommandWithParams->SetParameterInfo(nParams,   
                                                     ParamOrdinals,   
                                                     ParamBindInfo))) {  
      cout << "Failed in setting parameter information.(SetParameterInfo)\n";  
      goto EXIT;  
   }  
  
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
   }  
  
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
   hr = pICommandWithParams->QueryInterface(IID_IAccessor, (void**)&pIAccessor);  
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
   if (FAILED(hr = pICommandText->Execute( NULL,   
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
  
   // This result set is not important, so release it without processing.  
   pIRowset->Release();  
  
   printf("After processing the result set...\n");  
   printf("  Return value = %d\n", sprocparams.lReturnValue);  
   printf("  Output parameter value = %d\n\n", sprocparams.outParam);  
  
   // Release memory.  
   pIAccessor->ReleaseAccessor(hAccessor, NULL);  
   pIAccessor->Release();  
   pICommandWithParams->Release();  
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
   if (pICommandWithParams != NULL)  
      pICommandWithParams->Release();  
   if (pICommandText != NULL)  
      pICommandText->Release();  
   if (pIDBCreateCommand != NULL)  
      pIDBCreateCommand->Release();  
   if (pIDBCreateSession != NULL)  
      pIDBCreateSession->Release();  
   if (pIDBInitialize != NULL)  
      if (FAILED(pIDBInitialize->Uninitialize()))  
         // Uninitialize is not required, but it fails if an interface has not   
         // been released.  This can be used for debugging.  
         cout << "Problem in uninitializing.\n";  
      pIDBInitialize->Release();  
  
   CoUninitialize();  
}  
  
void InitializeAndEstablishConnection() {      
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.      
   hr = CoCreateInstance( CLSID_SQLNCLI11,   
                          NULL,   
                          CLSCTX_INPROC_SERVER,IID_IDBInitialize,   
                          (void **) &pIDBInitialize);  
  
   if (FAILED(hr))  
      cout << "Failed in CoCreateInstance().\n";  
  
   // Initialize the property values needed to establish the connection.  
   for (i = 0 ; i < nInitProps ; i++ )  
      VariantInit(&InitProperties[i].vValue);  
  
   //Specify server name.  
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
  
   // Properties are set, construct the DBPROPSET structure (rgInitPropSet) used to pass   
   // an array of // DBPROP structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties = 4;  
   rgInitPropSet[0].rgProperties = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface( IID_IDBProperties, (void **)&pIDBProperties);  
   if ( FAILED(hr))  
      cout << "Failed to obtain IDBProperties interface.\n";  
  
   hr = pIDBProperties->SetProperties( nPropSet, rgInitPropSet);  
   if (FAILED(hr))   
      cout << "Failed to set initialization properties.\n";  
  
   pIDBProperties->Release();  
  
   // Now establish a connection to the data source.  
   if ( FAILED(pIDBInitialize->Initialize()) )  
      cout << "Problem in initializing.\n";  
}  
```  
  
```  
USE AdventureWorks  
DROP PROCEDURE myProc  
GO  
```  
  
## <a name="see-also"></a>参照  
 [結果の操作方法に関するトピックを処理&#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/results/processing-results-how-to-topics-ole-db.md)  
  
  
