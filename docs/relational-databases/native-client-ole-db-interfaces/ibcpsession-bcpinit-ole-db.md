---
title: "Ibcpsession::bcpinit (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords: BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: "24"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 43f82a0cb7a7634353d1de821ccabf3a51e70740
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPInit(   
      const wchar_t *pwszTable,  
      const wchar_t *pwszDataFile,  
      const wchar_t *pwszErrorFile,  
      int eDirection);  
```  
  
## <a name="remarks"></a>解説  
 **BCPInit**メソッドは、その他の一括コピー メソッドの前に呼び出す必要があります。 **BCPInit**メソッドは、ワークステーションの間でデータの一括コピーの必要な初期化を実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 **BCPInit**メソッドは、データベース ソースまたはターゲット テーブルのデータ ファイルではなく、構造を検査します。 また、データベース テーブル、ビュー、または SELECT 結果セット内の各列に基づいてデータ ファイルのデータ形式値を指定します。 このデータ形式値には、各列のデータ型、長さや NULL のインジケーターとターミネータのバイト文字列がデータ内に存在するかどうか、および固定長データ型の幅の指定などが含まれます。 **BCPInit**メソッドは、これらの値を次のように設定します。  
  
-   指定するデータ型は、データベース テーブル、ビュー、または SELECT 結果セット内の列のデータ型です。 データ型によって列挙[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたネイティブ データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイル (sqlncli.h)。 列挙される値の形式は、BCP_TYPE_XXX です。 データはそのコンピューターの形式で表されます。 つまり、integer データ型の列のデータは、データ ファイルを作成したコンピューターに基づいて、ビッグ エンディアンまたはリトル エンディアンの 4 バイト シーケンスで表されます。  
  
-   データベースのデータ型が固定長の場合は、データ ファイルのデータも固定長になります。 データを処理する一括コピー メソッド (たとえば、 [:bcpexec](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)) と同じデータベース テーブル、ビュー、または列の選択 で指定されるデータの長さにするデータ ファイル内のデータの長さはデータ行が解析一覧です。 たとえば、`char(13)` で定義されているデータベース列のデータは、ファイル内の各データ行に 13 文字で表す必要があります。 データベース列で NULL 値を許容する場合は、固定長データにプレフィックスとして NULL インジケーターを付けることができます。  
  
-   データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ ファイルでは、データベース テーブルの各列のデータがあります。 データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベース テーブル、ビュー、または SELECT 結果セットのすべての列からのデータは、データ ファイルにコピーされます。  
  
-   データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ ファイル内の列の序数位置は、データベース テーブルの列の序数位置と同じである必要があります。 データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **BCPExec**メソッドは、データベース テーブルの列の序数位置に基づいてデータを配置します。  
  
-   データベースのデータ型が可変長 (`varbinary(22)` など) の場合、またはデータベース列に NULL 値を格納できる場合は、データ ファイル内のデータにプレフィックスとして長さのインジケーターや NULL インジケーターを付けることができます。 インジケーターの幅は、データ型と一括コピーのバージョンによって異なります。 [Ibcpsession::bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)メソッド オプション BCP_OPTION_FILEFMT 以前の一括コピー データ ファイルと以降のバージョンを実行しているサーバー間の互換性を提供する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]かを示す、内のインジケーターの幅、データは、予想よりも幅の狭いです。  
  
> [!NOTE]  
>  指定されたデータ ファイルのデータ形式値を変更するには、使用、 [ibcpsession::bcpcolumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)メソッドです。  
  
 一括コピー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース オプションを設定してインデックスを含んでいないテーブル用に最適化することができます**select/bulkcopy**です。  
  
## <a name="arguments"></a>引数  
 *pwszTable*[in]  
 コピー操作の対象になるデータベース テーブルの名前を指定します。 名前には、データベース名や所有者名を含めることができます。 たとえば、"pubs.username.titles"、"pubs..titles"、"username.titles" のように指定できます。  
  
 eDirection 引数を BCP_DIRECTION_OUT に設定すると、pwszTable 引数をデータベース ビューの名前にすることができます。  
  
 EDirection 引数を BCP_DIRECTION_OUT に設定しを使用して、SELECT ステートメントを指定する場合、 **BCPControl**メソッドの前に、 **BCPExec**メソッドが呼び出されると、 *pwszTable*引数を NULL に設定する必要があります。  
  
 *pwszDataFile*[in]  
 コピー操作の対象になるユーザー ファイルの名前を指定します。  
  
 *pwszErrorFile*[in]  
 進行状況メッセージ、エラー メッセージ、およびユーザー ファイルからテーブルにコピーできなかった行のコピーを格納するエラー ファイルの名前を指定します。 場合、 *pwszErrorFile*引数が NULL に設定されている、エラー ファイルは使用されません。  
  
 *eDirection*[in]  
 コピー操作の方向として、BCP_DIRECTION_IN か BCP_DIRECTION _OUT のいずれかを設定します。 BCP_DIRECTION _IN はユーザー ファイルからデータベース テーブルへのコピーを示します。BCP_DIRECTION _OUT はデータベース テーブルからユーザー ファイルへのコピーを示します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました ' 詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 E_INVALIDARG  
 1 つ以上の引数が正しく指定されませんでした。 たとえば、無効なファイル名が指定されました。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
