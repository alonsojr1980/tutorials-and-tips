program STDIN_EXAMPLE;

{$APPTYPE CONSOLE}

uses
  Windows,
  SysUtils,
  Classes;

var
  STDIN_HND: Integer;
  STDIN: THandleStream;
  text: AnsiString;
begin
  STDIN_HND := GetStdHandle(STD_INPUT_HANDLE);
  try
    STDIN := THandleStream.Create(STDIN_HND);
    try
      SetLength(text, STDIN.Size);
      STDIN.ReadBuffer(Pointer(text)^, STDIN.Size);
      text := StringReplace(text, sLineBreak, '', [rfReplaceAll]);
      Write(text);
    finally
      STDIN.Free;
    end;
  finally
    CloseHandle(STDIN_HND);
  end;

end.
