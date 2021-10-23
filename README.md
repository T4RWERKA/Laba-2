# Laba-2
Лабораторная работа 2
program Project1;

{$APPTYPE CONSOLE}

{$R *.res}

uses
  System.SysUtils;

var
  i, j, Number, NumberOfFactors, NumberOfFactors1, AmountOfNumbers, PowerOfFactor: integer;


begin
  Write('Введите количество различных простых множителей в разложении числа: ');
  //Readln(NumberOfFactors);
  NumberOfFactors := 2;
  Write('Введите количество чисел, которые нужно вывести: ');
  //Readln(AmountOfNumbers);
  AmountOfNumbers := 100;
  i := 2;
  while AmountOfNumbers > 0 do
  begin
    NumberOfFactors1 := 0;
    Number := i * i - 1;
    j := 2;
    while (j < 1000) and (Number > 1) do
    begin
      if Number mod j = 0 then
      begin
        NumberOfFactors1 := NumberOfFactors1 + 1;
        while Number mod j = 0 do
          Number := Number div j;
      end;
      j := j + 1;
    end;
    if (NumberOfFactors1 = NumberOfFactors) and (Number = 1) then
    begin
      Number := i * i - 1;
      AmountOfNumbers := AmountOfNumbers - 1;
      Write(i * i - 1, ' = ');
//      j := 2;
//      while (j < 1000) and (Number > 1) do
      for j := 2 to Trunc(Sqrt(Number)) + 2 do
      begin
        if Number mod j = 0 then
        begin
          PowerOfFactor := 0;
          Write(j);
          while Number mod j = 0 do
          begin
            Number := Number div j;
            PowerOfFactor := PowerOfFactor + 1;
          end;
          if (PowerOfFactor > 1) then
            Write('^', PowerOfFactor);
          if Number > 1 then
            Write(' * ');
        end;
//        j := j + 1;
      end;
      Writeln;
    end;
    i := i + 1;
  end;
  Readln;
end.
