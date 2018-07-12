---
title: テーブル値パラメーターにデータを挿入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
ms.assetid: 9c1a3234-4675-40d3-b473-8df06208f880
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b868179079f74799e949e98346b17817a370a15
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414781"
---
# <a name="inserting-data-into-table-valued-parameters"></a>テーブル値パラメーターへのデータの挿入
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、2 つのテーブル値パラメーター行のデータを指定するコンシューマー モデルをサポートしています。 プッシュ モデルとプル モデル。 プル モデルを示すサンプルが使用できます。参照してください[SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)します。  
  
> [!NOTE]  
>  テーブル値パラメーターの列では、すべての行に既定値以外の値が格納されているか、すべての行に既定値が格納されているかのどちらかでなければなりません。 一部の行にだけ既定値を格納することはできません。 したがって、テーブル値パラメーターのバインドでは、テーブル値パラメーターの行セット列データに許容される状態値は DBSTATUS_S_ISNULL と DBSTATUS_S_OK だけです。 DBSTATUS_S_DEFAULT ではエラーが発生し、バインド状態値が DBSTATUS_E_BADSTATUS に設定されます。  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a>プッシュ モデル (メモリ内のすべてのテーブル値パラメーターのデータを読み込む)  
 プッシュ モデルは、パラメーターのセット (つまり、icommand::execute で DBPARAMS パラメーター) の使用と似ています。 プッシュ モデルは、IRowset インターフェイスのカスタマイズされた実装を持たないテーブル値パラメーター行セット オブジェクトを使用する場合にのみ使用されます。 テーブル値パラメーターの行セット内の行数が少なく、アプリケーションに高いメモリ負荷がかからないことが見込まれる場合は、プッシュ モデルをお勧めします。 プッシュ モデルは、プル モデルよりも簡単な方法です。このモデルでは、コンシューマー アプリケーションに対し、標準的な OLE DB アプリケーションで現在一般的である以上の機能は要求されません。  
  
 コンシューマーは、コマンドを実行する前に、すべてのテーブル値パラメーターのデータをプロバイダーに提供します。 コンシューマーは、データを提供するために、各テーブル値パラメーター用にテーブル値パラメーターの行セット オブジェクトを作成します。 テーブル値パラメーターの行セット オブジェクトでは、行セットの挿入、設定、および削除の各操作が公開されます。このような操作は、コンシューマーがテーブル値パラメーターのデータを操作する際に使用します。 プロバイダーでは、実行時にこのテーブル値パラメーターの行セット オブジェクトからデータをフェッチします。  
  
 テーブル値パラメーターの行セット オブジェクトがコンシューマーに提供されると、コンシューマーはそのオブジェクトを行セット オブジェクトとして処理できます。 コンシューマーは、icolumnsinfo::getcolumninfo または icolumnsrowset::getcolumnsrowset インターフェイス メソッドを使用して、(型、最大の長さ、有効桁数、およびスケール) は、各列の型情報を取得できます。 その後、コンシューマーはアクセサーを作成してデータのバインドを指定します。 次に、データ行をテーブル値パラメーターの行セットに挿入します。 これは、irowsetchange::insertrow を使用して行うことができます。 Irowsetchange::setdata または irowsetchange::deleterows こともでき、テーブル値パラメーター行セット オブジェクトのデータを操作する必要がある場合。 テーブル値パラメーターの行セット オブジェクトは、ストリーム オブジェクトと同様に参照数がカウントされます。  
  
 Icolumnsrowset::getcolumnsrowset を使用する場合は、後続の呼び出し、結果の列の行セット オブジェクトの irowset::getnextrows、irowset::getdata、および::releaserows メソッドがあります。  
  
 後に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、コマンドの実行を開始すると、テーブル値パラメーターの値がこのテーブル値パラメーター行セット オブジェクトからフェッチされ、サーバーに送信します。  
  
 プッシュ モデルでは、コンシューマーによる作業は必要最小限になりますが、使用するメモリはプル モデルよりも多くなります。これは、すべてのテーブル値パラメーターのデータが実行時にメモリ内に存在する必要があるためです。  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a>プル モデル (要求時にコンシューマーからテーブル値パラメーターのデータを取得する)  
 プル モデルは、次の 2 つのシナリオで役立ちます。  
  
-   行をストリームする場合。  
  
-   別のプロバイダーの行セットがテーブル値パラメーターの値として使用されている場合。  
  
 プル モデルでは、コンシューマーが要求時にプロバイダーにデータを提供します。 この方法は、アプリケーションでデータの挿入が何度も行われ、メモリ内のテーブル値パラメーターの行セットのデータが過度にメモリにアクセスする場合に使用します。 複数の OLE DB プロバイダーが使用される場合、プル モデルでは、コンシューマーが任意の行セット オブジェクトをテーブル値パラメーターの値として提供できます。  
  
 プル モデルを使用するには、コンシューマーが行セット オブジェクトを独自に実装する必要があります。 コンシューマーが必要に、プロバイダーが、ITableDefinitionWithConstraints を通じて公開するテーブル値パラメーター行セット オブジェクトを集計するテーブル値パラメーター行セット (CLSID_ROWSET_TVP) でのプル モデルを使用する場合。CreateTableWithConstraints メソッドまたは iopenrowset::openrowset メソッド。 コンシューマー オブジェクトに期待されるのは、IRowset インターフェイスの実装をオーバーライドすることだけです。 次の関数をオーバーライドする必要があります。  
  
-   IRowset::GetNextRows  
  
-   IRowset::AddRefRows  
  
-   Irowset::getdata  
  
-   IRowset::ReleaseRows  
  
-   IRowset::RestartPosition  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、コンシューマーの行セット オブジェクトから一度に 1 つ以上の行を読み取り、テーブル値パラメーターのストリーミング動作をサポートします。 たとえば、ユーザーは、(メモリではなく) ディスクにテーブル値パラメーターの行セットのデータを保持し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーから要求されたときにディスクからデータを読み取る機能を実装する場合があります。  
  
 コンシューマーが通信するには、そのデータ形式[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダー iaccessor::createaccessor をテーブル値パラメーター行セット オブジェクトを使用しています。 プロバイダーは、データをコンシューマー バッファーから読み取る際に、既定以外の書き込み可能な列すべてを少なくとも 1 つのアクセサー ハンドルで使用できることを確認し、対応するハンドルを使用して列のデータを読み取ります。 あいまいさを回避するためには、テーブル値パラメーター行セットの列とバインド、一対一で対応が必要があります。 同じ列に対するバインドが重複すると、エラーが発生します。 また、各アクセサーが必要です、 *iOrdinal* DBBindings のシーケンス内のメンバー。 多くの irowset::getdata 呼び出し行あたりのアクセサーの数として、呼び出しの順序はの順序に基づきます*iOrdinal*より低い値からの値。  
  
 プロバイダーは、テーブル値パラメーターの行セット オブジェクトで公開されるインターフェイスのほとんどを実装することが期待されています。 コンシューマーでは、最小限のインターフェイス (IRowset) を使用して、行セット オブジェクトを実装します。 無計画な集計があるため、残りの必須の行セット オブジェクトのインターフェイスは、テーブル値パラメーターの行セット オブジェクトによって実装されます。  
  
 任意の OLE DB プロバイダー用に取得した行セット オブジェクトなどの他の行セット オブジェクトの場合、コンシューマーが提供した行セットは、OLE DB の仕様で指定されているとおり、必須の行セット オブジェクトのインターフェイスすべてを実装する必要があります。  
  
 実行時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは行セット オブジェクトにコールバックし、行をフェッチして列のデータを読み取ります。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して、 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
