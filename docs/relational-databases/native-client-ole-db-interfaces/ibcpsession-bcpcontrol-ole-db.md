---
title: Ibcpsession::bcpcontrol (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPControl (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPControl method
ms.assetid: d58f3fe1-45e3-4e46-8e9c-000971829d99
caps.latest.revision: 50
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8304b0797a4c9abcf01ce81f778920aba33ba445
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35701933"
---
# <a name="ibcpsessionbcpcontrol-ole-db"></a>IBCPSession::BCPControl (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー操作のオプションを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPControl(   
      int eOption,  
      void *iValue);  
```  
  
## <a name="remarks"></a>コメント  
 **BCPControl**メソッドは、一括コピーでは、コピー元のデータ ファイルとバッチ サイズは、最初と最後の行の番号をキャンセルする前に許容されるエラーの数などの一括コピー操作のさまざまな制御パラメーターを設定します。  
  
 また、このメソッドを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からデータを一括コピーするときに使用される SELECT ステートメントを指定することもできます。 設定することができます、 **eOption** BCP_OPTION_HINTS への引数と**iValue** SELECT ステートメントを含むワイド文字の文字列へのポインターを保持する引数。  
  
 指定できる値*eOption*は。  
  
|オプション|説明|  
|------------|-----------------|  
|BCP_OPTION_ABORT|既に実行中の一括コピー操作を停止します。 呼び出すことができます、 **BCPControl**メソッドを*eOption*引数に BCP_OPTION_ABORT から別のスレッドで実行されている一括コピー操作を停止します。 *IValue*引数は無視されます。|  
|BCP_OPTION_BATCH|バッチごとの行数を指定します。 既定値は 0 で、データが抽出されている場合は、テーブル内のすべての行を示す、またはユーザー データのすべての行はファイルにデータがコピーされているときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 BCP_OPTION_BATCH に 1 未満の値を指定すると、既定値にリセットされます。|  
|BCP_OPTION_DELAYREADFMT|ブール値の場合は、true に設定すると、 [ibcpsession::bcpreadfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)実行時に読み取り。 場合は false (既定値)、ibcpsession::bcpreadfmt がすぐには、フォーマット ファイルを読み取る。 シーケンス エラーが発生**BCP_OPTION_DELAYREADFMT**は true を呼び出す ibcpsession::bcpcolumns または ibcpsession::bcpcolfmt です。<br /><br /> 呼び出す場合にもシーケンス エラーが発生`IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)FALSE))`呼び出した後`IBCPSession::BCPControl(BCPDELAYREADFMT, (void *)TRUE)`および ibcpsession::bcpwritefmt です。<br /><br /> 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。|  
|BCP_OPTION_FILECP|*IValue*引数には、データ ファイルのコード ページの数が含まれています。 1252 など、コード ページの数または 850、またはその値は次のいずれかを指定できます。<br /><br /> BCP_FILECP_ACP を指定すると、ファイル内のデータには、クライアントの Microsoft Windows&#xAE; コード ページが使用されます。<br /><br /> BCP_FILECP_OEMCP を指定すると、ファイル内のデータには、クライアントの OEM コード ページ (既定) が使用されます。<br /><br /> BCP_FILECP_RAW を指定すると、ファイル内のデータには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコード ページが使用されます。|  
|BCP_OPTION_FILEFMT|データ ファイル形式のバージョン番号を指定します。 80 ([!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)])、90 ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)])、100 ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] または [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)])、110 ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)])、または 120 ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) を指定できます。 120 が既定値です。 このオプションは、以前のバージョンのサーバーでサポートされていた形式でデータをエクスポートおよびインポートする際に便利です。  たとえば、データをインポートする内のテキスト列から取得、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]のサーバーに、 **varchar (max)** 内の列、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]以降のサーバー 80 を指定する必要があります。 同様に、データのエクスポート中に 80 を指定する場合、 **varchar (max)** 列、保存されるのでにテキスト列を保存する場合と同じように、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]書式設定、およびのテキスト列にインポートすることができます、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サーバー。|  
|BCP_OPTION_FIRST|ファイルまたはテーブルにコピーするデータの先頭行を指定します。 既定値は 1 です。1 未満の値を指定すると、このオプションは既定値にリセットされます。|  
|BCP_OPTION_FIRSTEX|BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最初の行を指定します。<br /><br /> BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最初の行を指定します。<br /><br /> *IValue*値を含む符号付き 64 ビット整数のアドレスを指定するパラメーターが必要です。 BCPFIRSTEX に渡すことができる最大値は 2^63-1 です。|  
|BCP_OPTION_FMTXML|XML 形式でフォーマット ファイルが生成されることを指定する場合に使用します。 既定では、このオプションは無効で、フォーマット ファイルはテキスト ファイルとして保存されます。 XML フォーマット ファイルにより柔軟性が向上しますが、いくつか制約も追加されます。 たとえば、以前のフォーマット ファイルでは、1 つのフィールドにプレフィックスとターミネータを同時に指定できましたが、XML フォーマット ファイルでは指定できません。<br /><br /> 注: XML フォーマット ファイルはのみサポートされている場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と共にツールがインストールされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client です。|  
|BCP_OPTION_HINTS|*IValue*引数はワイド文字の文字列へのポインターを格納します。 ポインターが指す文字列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一括コピー処理ヒント、または結果セットを返す [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定します。 複数の結果セットを返す [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定すると、1 つ目の結果セット以外はすべて無視されます。|  
|BCP_OPTION_KEEPIDENTITY|ときに、 *iValue*引数が TRUE に設定されている、このオプションは、一括コピーの方法が指定されているデータ値を挿入することを指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列 identity 制約を定義します。 入力ファイルには ID 列の値を指定する必要があります。 このオプションを設定しないと、挿入される行に対して新しい ID 値が生成されます。 ファイル内に存在する ID 列用のデータはすべて無視されます。|  
|BCP_OPTION_KEEPNULLS|ファイル内の空のデータ値を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルで NULL 値に変換するかどうかを指定します。 ときに、 *iValue*引数が TRUE に設定されている空の値は NULL に変換されます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 既定では、空の値は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列の既定値 (存在する場合) に変換されます。|  
|BCP_OPTION_LAST|コピーする最終行を指定します。 既定では、すべての行をコピーします。 1 未満の値を指定すると、このオプションは既定値にリセットされます。|  
|BCP_OPTION_LASTEX|BCP out 操作の場合は、データ ファイルにコピーするための、データベース テーブルの最後の行を指定します。<br /><br /> BCP in 操作の場合は、データベース テーブルにコピーするための、データ ファイルの最後の行を指定します。<br /><br /> *IValue*値を含む符号付き 64 ビット整数のアドレスを指定するパラメーターが必要です。 BCPLASTEX に渡すことができる最大値は 2^63-1 です。|  
|BCP_OPTION_MAXERRS|一括コピー操作が失敗するまでに発生してもかまわないエラーの数を指定します。 既定値は 10 です。 1 未満の値を指定すると、このオプションは既定値にリセットされます。 一括コピーでは、最大 65,535 個のエラーが許容されます。 このオプションに 65,535 を超える値を設定しようとすると、65,535 が設定されます。|  
|BCP_OPTION_ROWCOUNT|現在 (または最後) の BCP 操作で処理された行数を返します。|  
|BCP_OPTION_TEXTFILE|データ ファイルは、バイナリ ファイルではなく、テキスト ファイルです。 BCP では、データ ファイルの先頭 2 バイトに含まれる Unicode バイト マーカーをチェックして、テキスト ファイルが Unicode 形式かどうかを検出します。|  
|BCP_OPTION_UNICODEFILE|このオプションに TRUE を設定して、入力ファイルが Unicode ファイル形式であることを指定します。|  
  
## <a name="arguments"></a>引数  
 *eOption*[in]  
 上記の「解説」で示したいずれかのオプションに設定します。  
  
 *iValue*[in]  
 指定された値*eOption*です。 *IValue*引数には、整数値を 64 ビット値に拡張できるように void ポインターにキャストします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドは、この関数を呼び出す前に呼び出されませんでした。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
