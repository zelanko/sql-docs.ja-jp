---
title: "LocalDBGetInstanceInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LocalDBGetInstanceInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 231706f5-26c6-42eb-ab47-315df6b8f824
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a341f47874f470697a6a7b6486015e4a7a4cbdca
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="localdbgetinstanceinfo-function"></a>LocalDBGetInstanceInfo 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  指定した SQL Server Express LocalDB インスタンスの情報を返します。たとえば、存在するかどうか、使用する LocalDB バージョン、実行中かどうかなどです。  
  
 情報が返されます、**構造体**という**LocalDBInstanceInfo**、次の定義を持ちます。  
  
```  
typedef struct _LocalDBInstanceInfo  
{  
      // Contains the size of the LocalDBInstanceInfo struct  
      DWORD  cbLocalDBInstanceInfoSize;  
  
      // Holds the instance name  
      TLocalDBInstanceNamewszInstanceName;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // TRUE if the instance configuration registry is corrupted, FALSE otherwise  
      BOOLbConfigurationCorrupted;  
  
      // TRUE if the instance is running at the moment, FALSE otherwise  
      BOOL   bIsRunning;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
  
      // Holds the date and time when the instance was started for the last time  
      FILETIME ftLastStartUTC;  
  
      // Holds the name of the TDS named pipe to connect to the instance  
      WCHARwszConnection;  
  
      // TRUE if the instance is shared, FALSE otherwise  
      BOOLbIsShared;  
  
      // Holds the shared name for the instance (if the instance is shared)  
      TLocalDBInstanceNamewszSharedInstanceName;  
  
      // Holds the SID of the instance owner (if the instance is shared)  
      WCHARwszOwnerSID;   
  
      // TRUE if the instance is Automatic, FALSE otherwise  
      BOOLbIsAutomatic;  
} LocalDBInstanceInfo;  
  
```  
  
 **ヘッダー ファイル:** sqlncli.h  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LocalDBGetInstanceInfo(  
           PCWSTR wszInstanceName,  
           PLocalDBInstanceInfo pInstanceInfo,  
           DWORD dwInstanceInfoSize   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 *wszInstanceName*  
 [入力] インスタンス名。  
  
 *pInstanceInfo*  
 [出力] LocalDB インスタンスについての情報を格納するバッファー。  
  
 *dwInstanceInfoSize*  
 [入力]サイズを保持する、 *InstanceInfo*バッファー。  
  
## <a name="returns"></a>返します。  
 S_OK  
 関数が正常に実行されました。  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB は、コンピューターにインストールされていません。  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 指定した 1 つまたは複数の入力パラメーターが無効です。  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 指定したインスタンス名は無効です。  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 インスタンスは存在しません。  
  
 [LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG](../../relational-databases/express-localdb-error-messages/localdb-error-instance-folder-path-too-long.md)  
 インスタンスを格納するパスの長さが MAX_PATH を超過しています。  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_FOLDER](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-folder.md)  
 インスタンス フォルダーにアクセスできません。  
  
 [LOCALDB_ERROR_CANNOT_ACCESS_INSTANCE_REGISTRY](../../relational-databases/express-localdb-error-messages/localdb-error-cannot-access-instance-registry.md)  
 インスタンス レジストリにアクセスできません。  
  
 [LOCALDB_ERROR_INSTANCE_CONFIGURATION_CORRUPT](../../relational-databases/express-localdb-error-messages/localdb-error-instance-configuration-corrupt.md)  
 インスタンス構成が破損しています。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 予期しないエラーが発生しました。 詳細をイベント ログで確認してください。  
  
## <a name="details"></a>詳細  
 導入根拠、**構造体**サイズ引数 (*lpInstanceInfoSize*) を返す別のバージョンの API を有効にするのには、 **LocalDBInstanceInfostruct**、効果的に上位および下位互換性を有効にします。  
  
 場合、**構造体**サイズ引数 (*lpInstanceInfoSize*) の既知のバージョンのサイズと一致する、 **LocalDBInstanceInfostruct**、そのバージョンの**構造体**が返されます。 それ以外の場合、LOCALDB_ERROR_INVALID_PARAMETER が返されます。  
  
 典型的な例**LocalDBGetInstanceInfo** API の使用率が次のように検索します。  
  
```  
LocalDBInstanceInfo ii;  
LocalDBInstanceInfo(L”Test”, &ii, sizeof(LocalDBInstanceInfo));  
  
```  
  
 LocalDB API を使用するコード サンプルは、次を参照してください。 [SQL Server Express LocalDB リファレンス](../../relational-databases/sql-server-express-localdb-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
