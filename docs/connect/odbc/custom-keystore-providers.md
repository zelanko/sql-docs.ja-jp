---
title: "カスタム キー ストア プロバイダー |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
caps.latest.revision: 1
ms.author: v-chojas
manager: jhubbard
author: MightyPen
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd6d86df2ec743376af34ac93d8b746bbe0a6eb3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="custom-keystore-providers"></a>カスタム キー ストア プロバイダー
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>概要

SQL Server 2016 の列の暗号化機能には、暗号化された列暗号化キー (ECEKs)、サーバーに保存するクライアントで取得し、暗号化された列に格納されているデータにアクセスするために列暗号化キー (CEKs) に復号化が必要です。 ECEKs はで列マスター_キー (Cmk) を暗号化され、CMK のセキュリティは、列の暗号化のセキュリティにとって重要です。 したがって、CMK を安全な場所に保存するか列暗号化キー ストア プロバイダーの目的は、ODBC ドライバーに安全にアクセスできるように、インターフェイスには、Cmk が格納されているためです。 独自のセキュリティで保護された記憶域を持つユーザーの場合は、カスタム キー ストア プロバイダーのインターフェイスは、CEK の暗号化と復号化を実行するために使用する ODBC ドライバーの CMK の記憶域をセキュリティで保護へのアクセスを実装するためフレームワークを提供します。

各キー ストア プロバイダーは、格納し、1 つを管理またはプロバイダーのキーのパスの形式の文字列によって識別され、複数の Cmk 定義します。 これには、プロバイダーによって定義された文字列も、暗号化アルゴリズムと共に使用できます、CEK の暗号化を使用して ECEK の復号化を実行します。 データベースの暗号化メタデータに、アルゴリズム、およびを使用して ECEK と、プロバイダーの名前が格納されています。参照してください[CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md)と[CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md)詳細についてはします。 そのため、キー管理の 2 つの基本的な操作には。

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

ここで、`CEKeystoreProvider_name`特定の列暗号化キー ストア プロバイダー (CEKeystoreProvider) を識別するため、CEKeystoreProvider によって (E) CEK の暗号化/暗号解除に使用されるために、その他の引数。 アルゴリズムとを使用して ECEK 値が、CEK メタデータによって提供されるときに、keypath と名前は、CMK メタデータによって提供されます。 複数のキー ストア プロバイダーは、既定の組み込みプロバイダーと共に存在する可能性があります。 CEK を必要とする操作を実行時に、ドライバーは CMK メタデータを使用して、名前で適切なキー ストア プロバイダーを検索し、として表現できますが、復号化操作を実行します。

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

ドライバーに Cek を暗号化する必要はありませんが、キーの管理ツールが CMK 作成およびローテーション; などの操作を実装するために必要があります。これは、逆の操作を実行する必要があります。

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>CEKeyStoreProvider インターフェイス

このドキュメントは、CEKeyStoreProvider インターフェイスを詳しく説明します。 このインターフェイスを実装するキー ストア プロバイダーは、SQL Server 用 Microsoft ODBC ドライバーで使用できます。 CEKeyStoreProvider 実装者は、ドライバーで使用可能なカスタム キー ストア プロバイダーを開発するのにこのガイドを使用できます。

キー ストア プロバイダー ライブラリは ("プロバイダー") は、ODBC ドライバーで読み込むことができます、ダイナミック リンク ライブラリを 1 つまたは複数のキー ストア プロバイダーが含まれています。 シンボル`CEKeystoreProvider`プロバイダー ライブラリによってエクスポートする必要があり、null で終わる配列へのポインターのアドレスでなければ`CEKeystoreProvider`構造体をライブラリ内のキー ストア プロバイダーごとに 1 つです。

A`CEKeystoreProvider`構造体は、1 つのキー ストア プロバイダーのエントリ ポイントを定義します。

```
typedef struct CEKeystoreProvider {
    wchar_t *Name;
    int (*Init)(CEKEYSTORECONTEXT *ctx, errFunc *onError);
    int (*Read)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int *len);
    int (*Write)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len);
    int (*DecryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *ecek,
                        unsigned short ecekLen,
                        unsigned char **cekOut,
                        unsigned short *cekLen);
    int (*EncryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *cek,
                        unsigned short cekLen,
                        unsigned char **ecekOut,
                        unsigned short *ecekLen);
    void (*Free)();
} CEKEYSTOREPROVIDER;
```

|フィールド名|Description|
|:--|:--|
|`Name`|キー ストア プロバイダーの名前。 このライブラリ存在しないか、ドライバーが読み込まれたその他のキー ストア プロバイダーと同じできません。 Null で終わる、ワイド-文字 * 文字列。|
|`Init`|初期化関数。 初期化関数が必要ない場合は、このフィールドを null にすることがあります。|
|`Read`|プロバイダーは、関数を読み取る。 必要でない場合は null にすることがあります。|
|`Write`|プロバイダーの書き込み機能。 読み取りが null でないかどうかに必要です。 必要でない場合は null にすることがあります。|
|`DecryptCEK`|使用して ECEK 復号化の関数。 この関数は、キー ストア プロバイダーの存在の理由であり、null にできません。|
|`EncryptCEK`|CEK の暗号化関数。 ドライバーは、この関数を呼び出しませんが、キー管理ツールによってプログラムへのアクセスを使用して ECEK 作成を許可するものです。 必要でない場合は null にすることがあります。|
|`Free`|終了関数。 必要でない場合は null にすることがあります。|

Free、を除き、このインターフェイスのすべての関数が、パラメーターのペアをしている**ctx**と**onError**です。 前者は、エラーの報告、後者は使用中に、関数が呼び出されますコンテキストを識別します。 参照してください[コンテキスト](#context-association)と[Error Handling](#error-handling)の下の詳細についてはします。

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
プロバイダーによって定義された初期化関数のプレース ホルダー名です。 ドライバーは、プロバイダーは読み込まれてを使用して ECEK 暗号化解除または Read()/Write() を実行する必要がある時間を要求する前に 後に 1 回、この関数を呼び出します。 必要な初期化を行うには、この関数を使用します。 

|引数|Description|
|:--|:--|
|`ctx`|[入力]操作コンテキスト。|
|`onError`|[入力]エラー レポート関数。|
|`Return Value`|正常終了した場合、または失敗を示すには 0 以外を返します。|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

通信のプロバイダーによって定義された関数のプレース ホルダー名です。 ドライバーは、データを読み取る (以前の書き込み先) プロバイダーから SQL_COPT_SS_CEKEYSTOREDATA 接続属性を使用してアプリケーションをプロバイダーから任意のデータを読み取ることにより、アプリケーションを要求するときに、この関数を呼び出します。 参照してください[キー ストア プロバイダーと通信する](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers)詳細についてはします。

|引数|Description|
|:--|:--|
|`ctx`|[入力]操作コンテキスト。|
|`onError`|[入力]エラー レポート関数。|
|`data`|[出力]プロバイダーがアプリケーションによって読み取られるデータに書き込むバッファーへのポインター。 これは、CEKEYSTOREDATA 構造のデータ フィールドに対応します。|
|`len`|[InOut]長さの値へのポインター入力時に、これは、データ バッファーの最大長とプロバイダーは書き込めません以上 * len バイトです。 関数が戻るとき、プロバイダーを更新する必要があります * len で実際に書き込まれたバイト数。|
|`Return Value`|正常終了した場合、または失敗を示すには 0 以外を返します。|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
通信のプロバイダーによって定義された関数のプレース ホルダー名です。 ドライバーは、アプリケーションにより、アプリケーションで任意のデータ プロバイダーを書き込む SQL_COPT_SS_CEKEYSTOREDATA 接続属性を使用してプロバイダーにデータを書き込むために必要と、この関数を呼び出します。 参照してください[キー ストア プロバイダーと通信する](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers)詳細についてはします。

|引数|Description|
|:--|:--|
|`ctx`|[入力]操作コンテキスト。|
|`onError`|[入力]エラー レポート関数。|
|`data`|[入力]読み取りをプロバイダー向けのデータを格納するバッファーへのポインター。 これは、CEKEYSTOREDATA 構造のデータ フィールドに対応します。 このバッファーから len バイトを超えるプロバイダーに読み取りありません必要です。|
|`len`|[入力]データで使用できるバイト数。 これは、dataSize、CEKEYSTOREDATA 構造体のフィールドに対応します。|
|`Return Value`|正常終了した場合、または失敗を示すには 0 以外を返します。|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
使用して ECEK 復号化プロバイダーによって定義された関数のプレース ホルダーの名前です。 ドライバーを使用して ECEK CEK には、このプロバイダーに関連付けられている CMK によって暗号化された暗号化を解除するには、この関数を呼び出します。

|引数|Description|
|:--|:--|
|`ctx`|[入力]操作コンテキスト。|
|`onError`|[入力]エラー レポート関数。|
|`keyPath`|[入力]値、 [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md)メタデータ属性の指定を使用して ECEK によって参照されている CMK をします。 Null で終わるワイド-文字 * 文字列。 これは、は、このプロバイダーによって処理される CMK を識別するものです。|
|`alg`|[入力]値、[アルゴリズム](../../t-sql/statements/create-column-encryption-key-transact-sql.md)指定されたを使用して ECEK のメタデータの属性です。 Null で終わるワイド-文字 * 文字列。 これは、は、指定されたを使用して ECEK の暗号化に使用される暗号化アルゴリズムを識別するためのものです。|
|`ecek`|[入力]復号化を使用して ECEK へのポインター。|
|`ecekLen`|[入力]使用して ECEK の長さです。|
|`cekOut`|[出力]プロバイダーは、復号化されたを使用して ECEK にメモリを割り当てるものとし、そのアドレスを cekOut を指すポインターに書き込みます。 メモリを使用するには、このブロックを解放できる必要があります、 [LocalFree](https://msdn.microsoft.com/library/windows/desktop/aa366730(v=vs.85).aspx) (Windows) または (Linux または Mac) 関数を解放します。 プロバイダーを設定するものとメモリがありませんでしたエラーのために割り当てられているか、それ以外の場合場合、* cekOut を null ポインターです。|
|`cekLen`|[出力]プロバイダーは cekLen によって示されるアドレスの長さを書き込む、復号化されたを使用して ECEK が書き込んでいる * * cekOut です。|
|`Return Value`|正常終了した場合、または失敗を示すには 0 以外を返します。|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
CEK の暗号化プロバイダーによって定義された関数のプレース ホルダーの名前です。 ドライバーがこの関数を呼び出すし、ODBC インターフェイスによってその機能を公開していませんが、キー管理ツールによってプログラムへのアクセスを使用して ECEK 作成を許可するものです。

|引数|Description|
|:--|:--|
|`ctx`|[入力]操作コンテキスト。|
|`onError`|[入力]エラー レポート関数。|
|`keyPath`|[入力]値、 [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md)メタデータ属性の指定を使用して ECEK によって参照されている CMK をします。 Null で終わるワイド-文字 * 文字列。 これは、は、このプロバイダーによって処理される CMK を識別するものです。|
|`alg`|[入力]値、[アルゴリズム](../../t-sql/statements/create-column-encryption-key-transact-sql.md)指定されたを使用して ECEK のメタデータの属性です。 Null で終わるワイド-文字 * 文字列。 これは、は、指定されたを使用して ECEK の暗号化に使用される暗号化アルゴリズムを識別するためのものです。|
|`cek`|[入力]CEK を暗号化するへのポインター。|
|`cekLen`|[入力]CEK の長さです。|
|`ecekOut`|[出力]プロバイダーは暗号化された CEK にメモリを割り当てるものとし、そのアドレスを ecekOut を指すポインターに書き込みます。 メモリを使用するには、このブロックを解放できる必要があります、 [LocalFree](https://msdn.microsoft.com/library/windows/desktop/aa366730(v=vs.85).aspx) (Windows) または (Linux または Mac) 関数を解放します。 プロバイダーを設定するものとメモリがありませんでしたエラーのために割り当てられているか、それ以外の場合場合、* ecekOut を null ポインターです。|
|`ecekLen`|[出力]プロバイダーはいてはいけない ecekLen によって示されるアドレスに書き込まれますが、暗号化された CEK の長さに書き込む * * ecekOut です。|
|`Return Value`|正常終了した場合、または失敗を示すには 0 以外を返します。|

```
void (*Free)();
```
終了のプロバイダーによって定義された関数のプレース ホルダー名です。 ドライバーには、プロセスの通常の終了時にこの関数を呼び出すことがあります。

> [!NOTE]
> *ワイド文字列とは、SQL Server での格納方法により 2 バイト文字 (UTF-16) です。*


### <a name="error-handling"></a>エラー処理

プロバイダーの処理中にエラーが発生した可能性がありますにブール型の成功/失敗より具体的なドライバーにエラーの報告を許可するメカニズムが提供されます。 パラメーターの組み合わせを持つ関数の多く**ctx**と**onError**成功/失敗の戻り値だけでなく、この目的のために一緒に使用されます。

**Ctx**パラメーターは、プロバイダーの操作が行われるコンテキストを識別します。

**OnError**パラメーターは次のプロトタイプで、エラー レポート関数を指します。

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|引数|Description|
|:--|:--|
|`ctx`|[入力]エラーを報告するコンテキスト。|
|`msg`|[入力]レポートのエラー メッセージ。 Null で終わるワイド文字列です。 存在するパラメーター化された情報を許可するのには、この文字列がによって受け入れられるフォームのシーケンスを挿入の書式設定を含めることが、 [FormatMessage](https://msdn.microsoft.com/library/windows/desktop/ms679351(v=vs.85).aspx)関数。 拡張機能は、次のようにこのパラメーターによって指定可能性があります。|
|[...]|[入力]必要に応じて、メッセージの書式指定子に合わせて追加の可変個引数パラメーターです。|

エラーが発生した日時を報告するため、プロバイダーの呼び出しエラーが生じた場合、コンテキスト パラメーターを指定する関数に渡される、プロバイダーによって、ドライバーと省略可能な追加のパラメーターのエラー メッセージがある書式設定します。 プロバイダーは、1 つのプロバイダー関数の呼び出し内で連続して複数のエラー メッセージを投稿するこの関数複数回を呼び出すことがあります。 例:

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


`msg`通常ワイド文字列ではパラメーターが追加の拡張機能は使用できます。

使用して特別な定義済みの値のいずれかの IDS_MSG マクロで一般的なエラー メッセージが既に存在し、ドライバーでのローカライズの形式では利用可能性があります。 たとえば、プロバイダーは、メモリを割り当てに失敗した場合、 `IDS_S1_001` 「メモリ割り当てに失敗」メッセージを使用できます。

`onError(ctx, IDS_MSG(IDS_S1_001));`

エラーが、ドライバーで検出するには、プロバイダー関数はエラーを返す必要があります。 これが ODBC 操作のコンテキストで実行されるときに、ポストされたエラーは、標準の ODBC 診断メカニズムを使用して、接続やステートメントのハンドル アクセス可能になります (`SQLError`、 `SQLGetDiagRec`、および`SQLGetDiagField`)。


### <a name="context-association"></a>コンテキストの関連付け

`CEKEYSTORECONTEXT`エラー コールバックのコンテキストを提供するだけでなく、構造体は、プロバイダーの操作を実行する ODBC コンテキストを決定も使用できます。 これにより、データに関連付けるには、これらのコンテキストの各例: プロバイダーを接続ごとの構成を実装します。 この目的では、構造体には、環境、接続、およびステートメントのコンテキストに対応する 3 つの不透明なポインターが含まれています。

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```
|フィールド|Description|
|:--|:--|
|`envCtx`|環境コンテキスト。|
|`dbcCtx`|接続コンテキストです。|
|`stmtCtx`|ステートメントのコンテキスト。|

これらのコンテキストの各はこれ、中に同じではありません、対応する ODBC ハンドルとして使用できる一意の識別子としてハンドルの非透過の値: 場合処理*X*コンテキストの値に関連付けられて*Y*、し、他の環境、接続、またはステートメント ハンドルのないと同時に同時に存在する*X*のコンテキストの値を持つ*Y*、およびその他のコンテキスト値が関連付けられるなし処理*X*です。実行されているプロバイダーの操作がない場合、特定のハンドル コンテキスト (SQLSetConnectAttr 呼び出しを読み込んで、ステートメント ハンドルがないプロバイダーを構成するなど)、対応する構造体のコンテキスト値が null です。


## <a name="example"></a>例

### <a name="keystore-provider"></a>キー ストア プロバイダー

次のコードは、最小のキー ストア プロバイダー実装の例です。

```
/* Custom Keystore Provider Example

Windows:   compile with cl MyKSP.c /LD /MD /link /out:MyKSP.dll
Linux/Mac: compile with gcc -fshort-wchar -fPIC -o MyKSP.so -shared MyKSP.c

 */

#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#endif

#include <stdlib.h>
#include <sqltypes.h>
#include "msodbcsql.h"
#include <sql.h>
#include <sqlext.h>

int __stdcall KeystoreInit(CEKEYSTORECONTEXT *ctx, errFunc *onError) {
    printf("KSP Init() function called\n");
    return 1;
}

static unsigned char *g_encryptKey;
static unsigned int g_encryptKeyLen;

int __stdcall KeystoreWrite(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len) {
    printf("KSP Write() function called (%d bytes)\n", len);
    if (len) {
        if (g_encryptKey)
            free(g_encryptKey);
        g_encryptKey = malloc(len);
        if (!g_encryptKey) {
            onError(ctx, L"Memory Allocation Error");
            return 0;
        }
        memcpy(g_encryptKey, data, len);
        g_encryptKeyLen = len;
    }
    return 1;
}

// Very simple "encryption" scheme - rotating XOR with the key
int __stdcall KeystoreDecrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg,
    unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen) {
    unsigned int i;
    printf("KSP Decrypt() function called (keypath=%S alg=%S ecekLen=%u)\n", keyPath, alg, ecekLen);
    if (wcscmp(keyPath, L"TheOneAndOnlyKey")) {
        onError(ctx, L"Invalid key path");
        return 0;
    }
    if (wcscmp(alg, L"none")) {
        onError(ctx, L"Invalid algorithm");
        return 0;
    }
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
#ifndef _WIN32
    *cekOut = malloc(ecekLen);
#else
    *cekOut = LocalAlloc(LMEM_FIXED, ecekLen);
#endif
    if (!*cekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *cekLen = ecekLen;
    for (i = 0; i < ecekLen; i++)
        (*cekOut)[i] = ecek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

// Note that in the provider interface, this function would be referenced via the CEKEYSTOREPROVIDER
// structure. However, that does not preclude keystore providers from exporting their own functions,
// as illustrated by this example where the encryption is performed via a separate function (with a
// different prototype than the one in the KSP interface.)
#ifdef _WIN32
__declspec(dllexport)
#endif
int KeystoreEncrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError,
    unsigned char *cek, unsigned short cekLen,
    unsigned char **ecekOut, unsigned short *ecekLen) {
    unsigned int i;
    printf("KSP Encrypt() function called (cekLen=%u)\n", cekLen);
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
    *ecekOut = malloc(cekLen);
    if (!*ecekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *ecekLen = cekLen;
    for (i = 0; i < cekLen; i++)
        (*ecekOut)[i] = cek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

CEKEYSTOREPROVIDER MyCustomKSPName_desc = {
    L"MyCustomKSPName",
    KeystoreInit,
    0,
    KeystoreWrite,
    KeystoreDecrypt,
    0
};

#ifdef _WIN32
__declspec(dllexport)
#endif
CEKEYSTOREPROVIDER *CEKeystoreProvider[] = {
    &MyCustomKSPName_desc,
    0
};
```

### <a name="odbc-application"></a>ODBC アプリケーション

次のコードは、上記のキー ストア プロバイダーを使用するデモ アプリケーションです。 ときに実行していることを確認、プロバイダー ライブラリが、アプリケーションのバイナリ ファイルと同じディレクトリにあること、接続文字列を指定します (またはを含む DSN を指定します)、`ColumnEncryption=Enabled`設定します。

```
/*
 Example application for demonstration of custom keystore provider usage

Windows:   compile with cl /MD kspapp.c /link odbc32.lib
Linux/Mac: compile with gcc -o kspapp -fshort-wchar kspapp.c -lodbc -ldl
 
 usage: kspapp connstr

 */

#define KSPNAME L"MyCustomKSPName"
#define PROV_ENCRYPT_KEY "JHKCWYT06N3RG98J0MBLG4E3"

#include <stdio.h>
#include <stdlib.h>
#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#include <dlfcn.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include "msodbcsql.h"

/* Convenience functions */

int checkRC(SQLRETURN rc, char *msg, int ret, SQLHANDLE h, SQLSMALLINT ht) {
    if (rc == SQL_ERROR) {
        fprintf(stderr, "Error occurred upon %s\n", msg);
        if (h) {
            SQLSMALLINT i = 0;
            SQLSMALLINT outlen = 0;
            char errmsg[1024];
            while ((rc = SQLGetDiagField(
                ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
                || rc == SQL_SUCCESS_WITH_INFO) {
                fprintf(stderr, "Err#%d: %s\n", i, errmsg);
            }
        }
        if (ret)
            exit(ret);
        return 0;
    }
    else if (rc == SQL_SUCCESS_WITH_INFO && h) {
        SQLSMALLINT i = 0;
        SQLSMALLINT outlen = 0;
        char errmsg[1024];
        printf("Success with info for %s:\n", msg);
        while ((rc = SQLGetDiagField(
            ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
            || rc == SQL_SUCCESS_WITH_INFO) {
            fprintf(stderr, "Msg#%d: %s\n", i, errmsg);
        }
    }
    return 1;
}

void postKspError(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...) {
    if (msg > (wchar_t*)65535)
        wprintf(L"Provider emitted message: %s\n", msg);
    else
        wprintf(L"Provider emitted message ID %d\n", msg);
}

int main(int argc, char **argv) {
    char sqlbuf[1024];
    SQLHENV env;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLRETURN rc;
    unsigned char CEK[32];
    unsigned char *ECEK;
    unsigned short ECEKlen;
#ifdef _WIN32
    HMODULE hProvLib;
#else
    void *hProvLib;
#endif
    CEKEYSTORECONTEXT ctx = {0};
    CEKEYSTOREPROVIDER **ppKsp, *pKsp;
    int(__stdcall *pEncryptCEK)(CEKEYSTORECONTEXT *, errFunc *, unsigned char *, unsigned short, unsigned char **, unsigned short *);
    int i;
    if (argc < 2) {
        fprintf(stderr, "usage: kspapp connstr\n");
        return 1;
    }

    /* Load the provider library */
#ifdef _WIN32
    if (!(hProvLib = LoadLibrary("MyKSP.dll"))) {
#else
    if (!(hProvLib = dlopen("./MyKSP.so", RTLD_NOW))) {
#endif
        fprintf(stderr, "Error loading KSP library\n");
        return 2;
    }
#ifdef _WIN32
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)GetProcAddress(hProvLib, "CEKeystoreProvider"))) {
#else
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)dlsym(hProvLib, "CEKeystoreProvider"))) {
#endif
        fprintf(stderr, "The export CEKeystoreProvider was not found in the KSP library\n");
        return 3;
    }
    while (pKsp = *ppKsp++) {
        if (!memcmp(KSPNAME, pKsp->Name, sizeof(KSPNAME)))
            goto FoundProv;
    }
    fprintf(stderr, "Could not find provider in the library\n");
    return 4;
FoundProv:
    if (pKsp->Init && !pKsp->Init(&ctx, postKspError)) {
        fprintf(stderr, "Could not initialize provider\n");
        return 5;
    }
#ifdef _WIN32
    if (!(pEncryptCEK = (LPVOID)GetProcAddress(hProvLib, "KeystoreEncrypt"))) {
#else
    if (!(pEncryptCEK = dlsym(hProvLib, "KeystoreEncrypt"))) {
#endif
        fprintf(stderr, "The export KeystoreEncrypt was not found in the KSP library\n");
        return 6;
    }
    if (!pKsp->Write) {
        fprintf(stderr, "Provider does not support configuration\n");
        return 7;
    }

    /* Configure the provider with the key */
    if (!pKsp->Write(&ctx, postKspError, PROV_ENCRYPT_KEY, strlen(PROV_ENCRYPT_KEY))) {
        fprintf(stderr, "Error writing to KSP\n");
        return 8;
    }

    /* Generate a CEK and encrypt it with the provider */
    srand(time(0) ^ getpid());
    for (i = 0; i < sizeof(CEK); i++)
        CEK[i] = rand();

    if (!pEncryptCEK(&ctx, postKspError, CEK, sizeof(CEK), &ECEK, &ECEKlen)) {
        fprintf(stderr, "Error encrypting CEK\n");
        return 9;
    }

    /* Connect to Server */
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &env);
    checkRC(rc, "allocating environment handle", 2, 0, 0);
    rc = SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0);
    checkRC(rc, "setting ODBC version to 3.0", 3, env, SQL_HANDLE_ENV);
    rc = SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc);
    checkRC(rc, "allocating connection handle", 4, env, SQL_HANDLE_ENV);
    rc = SQLDriverConnect(dbc, 0, argv[1], strlen(argv[1]), NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    checkRC(rc, "connecting to data source", 5, dbc, SQL_HANDLE_DBC);
    rc = SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
    checkRC(rc, "allocating statement handle", 6, dbc, SQL_HANDLE_DBC);

    /* Create a CMK definition on the server */
    {
        static char cmkSql[] = "CREATE COLUMN MASTER KEY CustomCMK WITH ("
            "KEY_STORE_PROVIDER_NAME = 'MyCustomKSPName',"
            "KEY_PATH = 'TheOneAndOnlyKey')";
        printf("Create CMK: %s\n", cmkSql);
        SQLExecDirect(stmt, cmkSql, SQL_NTS);
    }

    /* Create a CEK definition on the server */
    {
        const char cekSqlBefore[] = "CREATE COLUMN ENCRYPTION KEY CustomCEK WITH VALUES ("
            "COLUMN_MASTER_KEY = CustomCMK,"
            "ALGORITHM = 'none',"
            "ENCRYPTED_VALUE = 0x";
        char *cekSql = malloc(sizeof(cekSqlBefore) + 2 * ECEKlen + 2); /* 1 for ')', 1 for null terminator */
        strcpy(cekSql, cekSqlBefore);
        for (i = 0; i < ECEKlen; i++)
            sprintf(cekSql + sizeof(cekSqlBefore) - 1 + 2 * i, "%02x", ECEK[i]);
        strcat(cekSql, ")");
        printf("Create CEK: %s\n", cekSql);
        SQLExecDirect(stmt, cekSql, SQL_NTS);
        free(cekSql);
#ifdef _WIN32
        LocalFree(ECEK);
#else
        free(ECEK);
#endif
    }

#ifdef _WIN32
    FreeLibrary(hProvLib);
#else
    dlclose(hProvLib);
#endif

    /* Create a table with encrypted columns */
    {
        static char *tableSql = "CREATE TABLE CustomKSPTestTable ("
            "c1 int,"
            "c2 varchar(255) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = CustomCEK, ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'))";
        printf("Create table: %s\n", tableSql);
        SQLExecDirect(stmt, tableSql, SQL_NTS);
    }

    /* Load provider into the ODBC Driver and configure it */
    {
        unsigned char ksd[sizeof(CEKEYSTOREDATA) + sizeof(PROV_ENCRYPT_KEY) - 1];
        CEKEYSTOREDATA *pKsd = (CEKEYSTOREDATA*)ksd;
        pKsd->name = L"MyCustomKSPName";
        pKsd->dataSize = sizeof(PROV_ENCRYPT_KEY) - 1;
        memcpy(pKsd->data, PROV_ENCRYPT_KEY, sizeof(PROV_ENCRYPT_KEY) - 1);
#ifdef _WIN32
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "MyKSP.dll", SQL_NTS);
#else
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "./MyKSP.so", SQL_NTS);
#endif
        checkRC(rc, "Loading KSP into ODBC Driver", 7, dbc, SQL_HANDLE_DBC);
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREDATA, (SQLPOINTER)pKsd, SQL_IS_POINTER);
        checkRC(rc, "Configuring the KSP", 7, dbc, SQL_HANDLE_DBC);
    }

    /* Insert some data */
    {
        int c1;
        char c2[256];
        rc = SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &c1, 0, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        rc = SQLBindParameter(stmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_VARCHAR, 255, 0, c2, 255, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        for (i = 0; i < 10; i++) {
            c1 = i * 10 + i + 1;
            sprintf(c2, "Sample data %d for column 2", i);
            rc = SQLExecDirect(stmt, "INSERT INTO CustomKSPTestTable (c1, c2) values (?, ?)", SQL_NTS);
            checkRC(rc, "Inserting rows query", 10, stmt, SQL_HANDLE_STMT);
        }
        printf("(Encrypted) data has been inserted into the [CustomKSPTestTable]. You may inspect the data now.\n"
            "Press Enter to continue...\n");
        getchar();
    }

    /* Retrieve the data */
    {
        int c1;
        char c2[256];
        rc = SQLBindCol(stmt, 1, SQL_C_LONG, &c1, 0, 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLBindCol(stmt, 2, SQL_C_CHAR, c2, sizeof(c2), 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLExecDirect(stmt, "SELECT c1, c2 FROM CustomKSPTestTable", SQL_NTS);
        checkRC(rc, "Retrieving rows query", 12, stmt, SQL_HANDLE_STMT);
        while (SQL_SUCCESS == (rc = SQLFetch(stmt)))
            printf("Retrieved data: c1=%d c2=%s\n", c1, c2);
        SQLFreeStmt(stmt, SQL_CLOSE);
        printf("Press Enter to clean up and exit...\n");
        getchar();
    }

    /* Clean up */
    {
        SQLExecDirect(stmt, "DROP TABLE CustomKSPTestTable", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN ENCRYPTION KEY CustomCEK", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN MASTER KEY CustomCMK", SQL_NTS);
        printf("Removed table, CEK, and CMK\n");
    }
    SQLDisconnect(dbc);
    SQLFreeHandle(SQL_HANDLE_DBC, dbc);
    SQLFreeHandle(SQL_HANDLE_ENV, env);
    return 0;
}

```

## <a name="see-also"></a>参照

[ODBC ドライバーで Always Encrypted を使用します。](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)

