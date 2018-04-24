---
title: ADO 履歴 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology: drivers
ms.topic: conceptual
helpviewer_keywords:
- ADO, what's new
ms.assetid: 667673f2-3151-432b-894a-3fc60b704ea4
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53cbc9dd9fe0f2043026345e3385bdcdb2075f39
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="ado-features-for-each-release"></a>ADO の各リリースの機能
このトピックでは、ADO、ADO MD および ADOX の各リリースで導入された新機能を示します。

## <a name="ado-60"></a>ADO 6.0
 ADO 6.0 は Windows vista、Windows Data Access Components (Windows DAC) 6.0 の一部として含まれています。 ADO 6.0 は、ADO 2.8 に相当する機能。

## <a name="ado-28"></a>ADO 2.8
 ADO 2.8 は、Windows XP および Windows Server 2003 では、一部の Microsoft Data Access Components (MDAC) 2.8 として含まれています。 MDAC 2.8 の再頒布可能パッケージのバージョンも利用できます。Windows 2000 のみにこの再頒布可能パッケージのバージョンをインストールすることに注意してください。 ADO 2.8 は、いくつかのセキュリティ関連の懸案事項を説明します。

 *信頼済みゾーンの外部ハード ドライブへのアクセスが許可されていません。*
ドメイン間スクリプト信頼されていないサイトが関係する、次の操作は無効になっています: **Stream.SaveToFile**、 **Stream.LoadFromFile**、 **Recordset.Save**、および**Recordset.Open**、と共に使用される、 **adCmdFile**フラグ、または、Microsoft OLE DB 永続化プロバイダー (MSPersist)。

 **Recordset.Open** *、***Recordset.Save** *、***Stream.SaveToFile** *、および***Stream.LoadFromFile***物理ファイルのみで動作します。* 
これらのメソッドでは、ファイル ハンドルが物理ファイルのみを指しているようになりましたことを確認します。

 **Recordset.ActiveCommand***HTML/ASP ページから呼び出されたときにエラーが返されます。*
これにより、**コマンド**誤用されるオブジェクト。

 *数***レコード セット***、入れ子になったによって返される***図形***コマンドには上限値です。*
入れ子になった shape コマンドは 512 の最大値を返すようになりました**レコード セット**です。 つまり、**図形**コマンドは、任意の深さでネスト不要になったことができます。 代わりに、最大レベルの深さは、512、各コマンドを実行する 1 つ (子) の場合**Recordset**です。 任意のレベルでは、場合、**図形**コマンドが複数返されます**レコード セット**、最大の深さのレベルは 512 未満になります。

## <a name="ado-27"></a>ADO 2.7
 *64 ビット プラットフォームのサポート*ADO 2.7 64 ビット プロセッサのサポートが導入されています。

## <a name="ado-26"></a>ADO 2.6
 **CubDef.GetSchemaObject***メソッド*ADO 2.6 以降では、ADO MD 取得できるオブジェクトで指定された一意の名前を使用して、 [UniqueName プロパティ (ADO MD)](../../ado/reference/ado-md-api/uniquename-property-ado-md.md)です。 親オブジェクトの名前は、既知である必要はありませんし、親のコレクションは、スキーマ オブジェクトを取得する事前設定する必要はありません。 参照してください[GetSchemaObject メソッド (ADO MD)](../../ado/reference/ado-md-api/getschemaobject-method-ado-md.md)です。

 *コマンド ストリーム*、**コマンド**オブジェクトでは、ストリームの形式でコマンドをサポートを使用する代わりに、 **CommandText**プロパティです。 [CommandStream プロパティ (ADO)](../../ado/reference/ado-api/commandstream-property-ado.md) XML テンプレートまたはアップデート グラムとしてを指定するために使用する、**コマンド**for SQL Server、Microsoft OLE DB プロバイダーで入力します。

 **Dialect***プロパティ* [Dialect](../../ado/reference/ado-api/dialect-property.md)構文を定義する新しいプロパティは、一般的な規則を文字列またはストリームを解析するプロバイダーを使用することです。

 **Command.Execute***メソッド*、[メソッドを実行する](../../ado/reference/ado-api/execute-method-ado-command.md)ADO の**コマンド**入力と出力にストリームを使用するオブジェクトが強化されました。

 *フィールド statusvalues*ユーザーを変更する場合、DB_E_ERRORSOCCURRED エラーが発生した場合、**フィールド**の**Recordset**、ADO に収まるようになりました、 **Field.Status**プロパティを適切なステータス情報を使用できるように、ユーザーの詳細については、どのような問題が発生しました。 参照してください[Status プロパティ (ADO フィールド)](../../ado/reference/ado-api/status-property-ado-field.md)です。

 **NamedParameters***プロパティ* [NamedParameters](../../ado/reference/ado-api/namedparameters-property-ado.md)の新しいプロパティ、**コマンド**という名前のオブジェクトを示す、プロバイダーを使用する必要がありますパラメーター。

 *ストリームの結果セット*ADO は、データ ソースからの結果セットを返すことができます、**ストリーム**ではなく、 **Recordset**オブジェクト。 Microsoft OLE DB プロバイダーの最新バージョンを使用して、SQL Server 用、する XML 結果が得られますプロバイダーから"の XML"クエリを実行します。 A**ストリーム**結果セットを受け取る、ソースとして"XML の"コマンドを使用して開くことができます。 参照してください[ストリームに結果セットを取得する](../../ado/guide/data/retrieving-resultsets-into-streams.md)です。

 *1 つの行の結果セット*、ADO**レコード**オブジェクト開くことができるコマンド文字列にまたは**コマンド**プロバイダーからの 1 行のデータを表すオブジェクト。 これにより、MDAC 2.6 プロバイダーによるパフォーマンスの向上。 参照してください[メソッド (ADO レコード) を開く](../../ado/reference/ado-api/open-method-ado-record.md)です。

## <a name="ado-25"></a>ADO 2.5
 **レコード***オブジェクト*ADO 2.5 が導入されています、**レコード**表示してから行を管理するオブジェクト、**レコード セット**またはデータ プロバイダー、またはオブジェクトのカプセル化します。ファイルやディレクトリなど、半構造化データです。

 **ストリーム***オブジェクト*ADO 2.5 にも導入されています、**ストリーム**バイナリまたはテキスト データのストリームを表すオブジェクト。

 *URL バインディング*ADO 2.5 がデータ ストア オブジェクトの名前に、接続文字列とコマンド テキストの代わりとして、URL の使用方法を紹介します。 既存の URL を使用できます**接続**と**レコード セット**、オブジェクトに新しいとして**レコード**と**ストリーム**オブジェクト。

 *URL のバインディングをサポートするデータ プロバイダー* ADO 2.5 に URL スキームを認識する OLE DB プロバイダーがサポートされています。 これには、Windows 2000 のファイル システムにアクセスし、既存の HTTP スキームを認識する Internet Publishing の OLE DB プロバイダーが含まれます。
