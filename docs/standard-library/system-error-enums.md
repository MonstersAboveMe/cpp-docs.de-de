---
title: '&lt;system_error&gt;-Klasse'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::errc
- system_error/std::io_errc
ms.assetid: b21321b7-404a-40de-8777-a85b77c6fa58
ms.openlocfilehash: 4e9d63854e937160d8e3cc617a61b0b9c1c75c48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412136"
---
# <a name="ltsystemerrorgt-enums"></a>&lt;system_error&gt;-Klasse

|||
|-|-|
|[errc](#errc)|[io_errc](#io_errc)|

## <a name="errc"></a> errc-Enumeration

Gibt symbolische Namen für alle Fehlercodemakros an, die von Posix in `<errno.h>` definiert sind.

class errc { address_family_not_supported = EAFNOSUPPORT, address_in_use = EADDRINUSE, address_not_available = EADDRNOTAVAIL, already_connected = EISCONN, argument_list_too_long = E2BIG, argument_out_of_domain = EDOM, bad_address = EFAULT, bad_file_descriptor = EBADF, bad_message = EBADMSG, broken_pipe = EPIPE, connection_aborted = ECONNABORTED, connection_already_in_progress = EALREADY, connection_refused = ECONNREFUSED, connection_reset = ECONNRESET, cross_device_link = EXDEV, destination_address_required = EDESTADDRREQ, device_or_resource_busy = EBUSY, directory_not_empty = ENOTEMPTY, executable_format_error = ENOEXEC, file_exists = EEXIST, file_too_large = EFBIG, filename_too_long = ENAMETOOLONG, function_not_supported = ENOSYS, host_unreachable = EHOSTUNREACH, identifier_removed = EIDRM, illegal_byte_sequence = EILSEQ, inappropriate_io_control_operation = ENOTTY, interrupted = EINTR, invalid_argument = EINVAL, invalid_seek = ESPIPE, io_error = EIO, is_a_directory = EISDIR, message_size = EMSGSIZE, network_down = ENETDOWN, network_reset = ENETRESET, network_unreachable = ENETUNREACH, no_buffer_space = ENOBUFS, no_child_process = ECHILD, no_link = ENOLINK, no_lock_available = ENOLCK, no_message_available = ENODATA, no_message = ENOMSG, no_protocol_option = ENOPROTOOPT, no_space_on_device = ENOSPC, no_stream_resources = ENOSR, no_such_device_or_address = ENXIO, no_such_device = ENODEV, no_such_file_or_directory = ENOENT, no_such_process = ESRCH, not_a_directory = ENOTDIR, not_a_socket = ENOTSOCK, not_a_stream = ENOSTR, not_connected = ENOTCONN, not_enough_memory = ENOMEM, not_supported = ENOTSUP, operation_canceled = ECANCELED, operation_in_progress = EINPROGRESS, operation_not_permitted = EPERM, operation_not_supported = EOPNOTSUPP, operation_would_block = EWOULDBLOCK, owner_dead = EOWNERDEAD, permission_denied = EACCES, protocol_error = EPROTO, protocol_not_supported = EPROTONOSUPPORT, read_only_file_system = EROFS, resource_deadlock_would_occur = EDEADLK, resource_unavailable_try_again = EAGAIN, result_out_of_range = ERANGE, state_not_recoverable = ENOTRECOVERABLE, stream_timeout = ETIME, text_file_busy = ETXTBSY, timed_out = ETIMEDOUT, too_many_files_open_in_system = ENFILE, too_many_files_open = EMFILE, too_many_links = EMLINK, too_many_synbolic_link_levels = ELOOP, value_too_large = EOVERFLOW, wrong_protocol_type = EPROTOTYPE, };

### <a name="remarks"></a>Hinweise

## <a name="io_errc"></a> io_errc-Enumeration

Gibt symbolische Namen für die Fehlerzustände in \<iostream> an. Kann verwendet werden, um [error_condition](../standard-library/error-condition-class.md)-Objekte zu erstellen, die mit dem Wert verglichen werden, der von der Funktion [ios_base::failure](../standard-library/ios-base-class.md#failure)`code()` zurückgegeben wird.

class io_errc { stream = 1 };

### <a name="remarks"></a>Hinweise

[std::make_error_code()](../standard-library/system-error-functions.md#make_error_code) und [std::make_error_condition()](../standard-library/system-error-functions.md#make_error_condition) sind für diese Enumeration überladen.

`ios_base::failure` kann Kategorien von Fehlercodes enthalten, die nicht `error_condition` sind.

### <a name="example"></a>Beispiel

```cpp
// io_errc.cpp
// cl.exe /nologo /W4 /EHsc /MTd

#include <iostream>

using namespace std;

int main()
{
    cin.exceptions(ios::failbit | ios::badbit);

    try {
        cin.rdbuf(nullptr); // throws io_errc::stream
    }
    catch (ios::failure& e) {
        cerr << "ios failure caught: ";
        if (e.code() == make_error_condition(io_errc::stream)) {
            cerr << "io_errc stream error condition" << endl;
        }
        else {
            cerr << "unmatched error condition code " << e.code() << endl;
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

[<system_error>](../standard-library/system-error.md)<br/>
