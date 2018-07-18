---
title: Ibcpsession::bcpinit (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11ddae5bacdd5428a4381ec034d9dc9f0f22b6b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413406"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
  一括コピー構造を初期化し、エラー チェックを実行して、データ ファイルとフォーマット ファイルの名前が正しいことを確認します。その後、それらのファイルを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a>コメント  
 **BCPInit**メソッドは、他の一括コピー メソッドの前に呼び出す必要があります。 **BCPInit**メソッドは、ワークステーションの間でデータの一括コピーの必要な初期化を実行し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 **BCPInit**メソッドは、データベース ソースまたはターゲット テーブルのデータ ファイルではなく構造を検査します。 また、データベース テーブル、ビュー、または SELECT 結果セット内の各列に基づいてデータ ファイルのデータ形式値を指定します。 このデータ形式値には、各列のデータ型、長さや NULL のインジケーターとターミネータのバイト文字列がデータ内に存在するかどうか、および固定長データ型の幅の指定などが含まれます。 **BCPInit**メソッドは、これらの値を次のように設定します。  
  
-   指定するデータ型は、データベース テーブル、ビュー、または SELECT 結果セット内の列のデータ型です。 データ型によって列挙[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたネイティブ データ型、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイル (sqlncli.h)。 列挙される値の形式は、BCP_TYPE_XXX です。 データはそのコンピューターの形式で表されます。 つまり、integer データ型の列のデータは、データ ファイルを作成したコンピューターに基づいて、ビッグ エンディアンまたはリトル エンディアンの 4 バイト シーケンスで表されます。  
  
-   データベースのデータ型が固定長の場合は、データ ファイルのデータも固定長になります。 データを処理する一括コピー メソッド (たとえば、 [:bcpexec](ibcpsession-bcpexec-ole-db.md)) と同じデータベース テーブル、ビュー、または SELECT 列で指定されたデータの長さにするデータ ファイル内のデータの長さのデータ行が解析リスト。 たとえば、`char(13)` で定義されているデータベース列のデータは、ファイル内の各データ行に 13 文字で表す必要があります。 データベース列で NULL 値を許容する場合は、固定長データにプレフィックスとして NULL インジケーターを付けることができます。  
  
-   データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ ファイルでは、データベース テーブルの各列のデータがあります。 データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベース テーブル、ビュー、または SELECT 結果セットのすべての列からデータがデータ ファイルにコピーされます。  
  
-   データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ ファイル内の列の序数位置は、データベース テーブルの列の序数位置と同じである必要があります。 データをコピーするときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **BCPExec**メソッドは、データベース テーブルの列の序数位置に基づいてデータを配置します。  
  
-   データベースのデータ型が可変長 (`varbinary(22)` など) の場合、またはデータベース列に NULL 値を格納できる場合は、データ ファイル内のデータにプレフィックスとして長さのインジケーターや NULL インジケーターを付けることができます。 インジケーターの幅は、データ型と一括コピーのバージョンによって異なります。 [Ibcpsession::bcpcontrol](ibcpsession-bcpcontrol-ole-db.md)メソッド オプション BCP_OPTION_FILEFMT 以前の一括コピー データ ファイルと以降のバージョンを実行しているサーバーの間の互換性を備えている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]かを示す、内のインジケーターの幅、データは、予想よりも幅の狭いです。  
  
> [!NOTE]  
>  データ ファイルに指定されたデータ形式値を変更するには、使用、 [ibcpsession::bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)メソッド。  
  
 一括コピー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース オプションを設定してインデックスを含んでいないテーブル用に最適化できます**select/bulkcopy**します。  
  
## <a name="arguments"></a>引数  
 *pwszTable*[in]  
 コピー操作の対象になるデータベース テーブルの名前を指定します。 名前には、データベース名や所有者名を含めることができます。 たとえば、"pubs.username.titles"、"pubs..titles"、"username.titles" のように指定できます。  
  
 eDirection 引数を BCP_DIRECTION_OUT に設定すると、pwszTable 引数をデータベース ビューの名前にすることができます。  
  
 EDirection 引数を BCP_DIRECTION_OUT に設定しを使用して SELECT ステートメントを指定する場合、 **BCPControl**メソッドの前に、 **BCPExec**メソッドを呼び出すと、 *pwszTable*引数を NULL に設定する必要があります。  
  
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
 プロバイダー固有のエラーが発生しました ' 詳細については、使用、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイス。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 E_INVALIDARG  
 1 つ以上の引数が正しく指定されませんでした。 たとえば、無効なファイル名が指定されました。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)  
  
  
