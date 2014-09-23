protected function setCode(array $tokens, $line = 0)
{
$this->tokens = $tokens;
$this->line = $line;
}


 protected function next()
{
while ($token = array_shift($this->tokens)) {
$this->line += substr_count($this->value($token), "\n");
if (is_array($token) && in_array($token[0], array(T_WHITESPACE, T_COMMENT, T_DOC_COMMENT))) {
continue;
}
return $token;
}
}
