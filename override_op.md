defmodule MyOp do

  @moduledoc """
  Override the multipy operator :*, let "<string>" * <number> be multipize the string.
  """

  defmacro __using__(_) do
    quote do
      import MyOp
      import Kernel, except: [*: 2]
    end
  end

  defmacro lv * rv when is_bitstring(lv) and is_integer(rv) and rv > 0 do
    list = append(lv,[],rv)
    quote do
      unquote(list)
    end
  end

  defmacro lv * rv do
    quote do
      unquote(lv) * unquote(rv)
    end
  end

  defp append(char, list, n) when n == 1 do
    [char|list] |> IO.chardata_to_string
  end

  defp append(char, list, n) when n > 1 do
    append(char, [char|list], n-1)
  end
end
