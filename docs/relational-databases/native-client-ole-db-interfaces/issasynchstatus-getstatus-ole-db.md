---
title: Issasynchstatus::getstatus (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSAsynchStatus::GetStatus (OLE DB)
apitype: COM
helpviewer_keywords:
- GetStatus method
ms.assetid: 354b6ee4-b5a1-48f6-9403-da3bdc911067
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d39998e41fd26bb2928290f62dd08fc54a0f567a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407864"
---
# <a name="issasynchstatusgetstatus-ole-db"></a>ISSAsynchStatus::GetStatus (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  非同期に実行されている操作の状態を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT GetStatus(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation,  
        DBCOUNTITEM *pulProgress,  
        DBCOUNTITEM *pulProgressMax,  
        DBASYNCHPHASE *peAsynchPhase,  
        LPOLESTR *ppwszStatusText);  
```  
  
## <a name="arguments"></a>引数  
 *hChapter*[in]  
 チャプター ハンドル。 ポーリングされているオブジェクトが行セット オブジェクトではないか、操作がチャプターに適用されない場合は、この引数を DB_NULL_HCHAPTER に設定する必要があります。プロバイダーでは、この設定が無視されます。  
  
 *eOperation*[in]  
 非同期状態が要求されている操作。 この引数には、  
  
 DBASYNCHOP_OPEN を設定する必要があります。コンシューマーは、この設定により、行セットを開くか行セットにデータを設定する非同期操作に関する情報、またはデータ ソース オブジェクトを初期化する非同期操作に関する情報を要求します。 プロバイダーが URL の直接バインドをサポートする OLE DB 2.5 に準拠したプロバイダーの場合、コンシューマーは、データ ソース、行セット、行、またはストリーム オブジェクトの初期化やデータ設定の非同期操作に関する情報を要求します。  
  
 *pulProgress*[out]  
 示される予想最大の基準とした非同期操作の現在の進行状況を返すメモリへのポインター、 *pulProgressMax*パラメーター。 意味の詳細については*pulProgress*の説明を参照して*peAsynchPhase*します。  
  
 場合*pulProgress* null ポインターの場合は、進行状況は返されません。  
  
 *pulProgressMax*[out]  
 予想最大値を返すメモリへのポインター、 *pulProgress*パラメーター。 この値は、このメソッドを呼び出すたびに変化することがあります。 意味の詳細については*pulProgressMax*の説明を参照して*peAsynchPhase*します。  
  
 場合*pulProgressMax* null ポインターの場合は、予想最大値は返されません。  
  
 *peAsynchPhase*[out]  
 非同期操作の進行状況に関する詳細情報を返すメモリへのポインター。 有効な値は次のとおりです。  
  
 DBASYNCHPHASE_INITIALIZATION は、オブジェクトが初期化フェーズにあることを示します。 引数*pulProgress*と*pulProgressMax*完了の推定の比率を示します。 オブジェクトはまだ完全に具体化されていません。 そのため、他のインターフェイスの呼び出しを試みると失敗したり、このオブジェクトのすべてのインターフェイスを使用できない場合があります。 非同期操作が呼び出しの結果が場合**icommand::execute**場合と、更新するコマンドは、削除、または行を挿入の*cParamSets*が 1 より大きい*pulProgress*と*pulProgressMax*パラメーターの 1 つのセットまたはパラメーター セットの完全な配列の進行状況を示す場合があります。  
  
 DBASYNCHPHASE_POPULATION は、オブジェクトが作成フェーズにあることを示します。 行セットは完全に初期化されていて、オブジェクトのすべてのインターフェイスを使用できますが、まだ行セットに追加されていない行が存在する場合があります。 中に*pulProgress*と*pulProgressMax*基づくことができる行のデータの数、一般に基づいている時間または行セットを作成するために必要な作業です。 そのため、呼び出し元では最終的な行数ではなく、処理にかかる時間の大まかな推定値としてこの情報を使用する必要があります。 このフェーズが返されるのは、行セットの設定中のみです。データ ソース オブジェクトの初期化中や、行を更新、削除、または挿入するコマンドの実行により返されることはありません。  
  
 DBASYNCHPHASE_COMPLETE は、オブジェクトのすべての非同期処理が完了したことを示します。 **Issasynchstatus::getstatus**操作の結果を示す HRESULT を返します。 通常、この HRESULT は、同期をとって操作を呼び出した場合に返される HRESULT です。 非同期操作が呼び出しの結果が場合**icommand::execute**更新、削除、または行を挿入するコマンドの*pulProgress*と*pulProgressMax*はコマンドによって影響を受ける行の合計数に等しい。 場合*cParamSets*が 1 より大きい、これは、すべての実行で指定されたパラメーターのセットを受けた行の合計数。 場合*peAsynchPhase* null ポインターの場合は、状態コードは返されません。  
  
 DBASYNCHPHASE_CANCELED は、オブジェクトの非同期処理が中止されたことを示します。 **Issasynchstatus::getstatus** DB_E_CANCELED が返されます。 非同期操作が呼び出しの結果が場合**icommand::execute**更新、削除、または行を挿入するコマンドの*pulProgress*がすべてのパラメーター セットの行の合計数と等しいキャンセルする前に、コマンドによって影響を受けます。  
  
 *ppwszStatusText*[入力/出力]  
 操作に関する詳細情報を保持するメモリへのポインター。 プロバイダーは、この値を使用して操作の異なる要素 (アクセス中のさまざまなリソースなど) を区別できます。 この文字列は、データ ソース オブジェクトの DBPROP_INIT_LCID プロパティに従ってローカライズされます。  
  
 場合*ppwszStatusText*が null 以外の入力に、プロバイダーがで識別される特定の要素に関連付けられている状態を返します*ppwszStatusText*します。 場合*ppwszStatusText*の要素を示しません*eOperation*、して S_OK を返します、 *pulProgress*と*pulProgressMax*同じ値に設定します。 プロバイダーがテキスト識別子に基づいて要素を区別しない場合は設定*ppwszStatusText*全体の操作について NULL を返しますに場合は、 *ppwszStatusText*は null 以外の入力に、プロバイダーが離れる*ppwszStatusText*変更します。  
  
 場合*ppwszStatusText*がプロバイダーのセットの入力で null *ppwszStatusText*などの情報が使用できない場合、または場合、または NULL に、操作に関する詳細を示す値を**Issasynchstatus::getstatus**はエラーを返します。 ときに*ppwszStatusText*プロバイダーの入力で null がステータス文字列のメモリを割り当てるし、このメモリをアドレスを返します。 コンシューマーでこのメモリを解放する**imalloc::free**ときに、不要になったに文字列が必要です。  
  
 場合*ppwszStatusText*値が NULL の入力、ステータス文字列が返されない、およびプロバイダーは、一般に、操作または操作の任意の要素に関する情報を返します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドから正常に値が返されました。  
  
-   場合*peAsynchPhase*が DBASYNCHPHASE_INITIALIZATION と等しいオブジェクトがまだ完全に初期化されていません。 いずれかを呼び出すしようとしています。 他のインターフェイスが失敗すると、インターフェイスの完全なセットをオブジェクトで利用できない可能性があります。  
  
-   場合*peAsynchPhase*が DBASYNCHPHASE_POPULATION と等しい行セットが完全に初期化しインターフェイスの完全な範囲は、オブジェクトで使用できます。 ただし、する可能性があります、行セットに設定されていない追加の行。  
  
-   場合*peAsynchPhase*が dbasynchphase_complete オブジェクトのすべての非同期処理が完了します。 オブジェクトは、完全に初期化され、データが設定されています。  
  
 DB_E_CANCELED  
 行セットの設定中に非同期操作が取り消されたことを示します。 この場合、データ設定操作は停止されますが、既に設定した行セットの行は有効なままです。  
  
 また、データ ソース オブジェクトの初期化中に非同期処理が取り消されたことを示している場合もあります。 この場合、データ ソース オブジェクトは初期化されていない状態です。  
  
 E_INVALIDARG  
 *HChapter*パラメーターが正しくありません。  
  
 E_UNEXPECTED  
 **Issasynchstatus::getstatus** 、データ ソース オブジェクトで呼び出されたと**idbinitialize::initialize**データ ソース オブジェクトで呼び出されていません。  
  
 **Issasynchstatus::getstatus** 、行セットに対して呼び出された**itransaction::commit**または**itransaction::abort**が呼び出されたオブジェクトはゾンビ状態とします。  
  
 **Issasynchstatus::getstatus**が初期化フェーズで非同期に取り消された行セットに対して呼び出されました。 行セットはゾンビ状態になります。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。  
  
## <a name="remarks"></a>コメント  
 **Issasynchstatus::getstatus**とまったく同じメソッドの動作は、 **idbasynchstatus::getstatus**点を除いてメソッド ソース オブジェクトのデータを初期化する場合は中止されます、E_UNEXPECTED が返されるではなくDB_E_CANCELED より (が[issasynchstatus::waitforasynchcompletion](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md) DB_E_CANCELED が返されます)。 これは、初期化の中止後、追加の初期化操作が試行される場合に備えて、データ ソース オブジェクトの状態が通常のゾンビ状態のままにならないためです。  
  
 行セットを初期化またはデータ設定する非同期操作では、このメソッドをサポートする必要があります。  
  
 表示されている場合、戻り値だけでなく**issasynchstatus::getstatus**操作の成否を示す、非同期操作を開始するメソッドによって返された HRESULT を返すことができます。  
  
 一部の非同期操作では、"完了" または "未完了" 以外の状態を返すことができません。 設定する必要があります*pulProgressMax* 1 の値に 0/1 または 1/1 のいずれかになるために、推定値では、オール_オア_ナッシングの粒度を示します。  
  
 プロバイダーが変わる可能性がある*pulProgressMax*の連続呼び出しでともこれは、タスクの完了の度合いの向上の推定値を反映している場合、以前よりも少ない比率を返します。  
  
 プロバイダーは、より正確な値を保証することが義務付けられているわけではありませんが、可能な場合は妥当な推定完了率を返すように設定されています。 この関数の主な目的は、ユーザーへの進行状況のフィードバックを提供することなので、このような動作によりユーザー インターフェイスの品質が向上します。 非表示で行われる、実行時間が長いタスクに対するフィードバックの品質を向上することで、ユーザーの満足度も向上します。  
  
 呼び出す**issasynchstatus::getstatus**初期化されたデータ ソース オブジェクトまたはデータが設定された行セット、またはの値を渡す*eOperation* 、DBASYNCHOP_OPEN 以外に S_OK を返します*pulProgress*と*pulProgressMax*同じ値に設定します。 場合**issasynchstatus::getstatus**が更新、削除、または行を挿入するコマンドの実行から作成されたオブジェクトで呼び出されます両方*pulProgress*と*pulProgressMax*コマンドによって影響を受ける行の総数を示します。  
  
## <a name="see-also"></a>参照  
 [非同期操作を実行します。](../../relational-databases/native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
